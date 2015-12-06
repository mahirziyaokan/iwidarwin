# sk\_buff #


## struct ##
```

  ,- skb->data
 |
 |    ETHERNET HEADER        ,-<-- PAYLOAD
 |                           |     14 bytes from skb->data
 |  2 bytes for Type --> ,T. |     (sizeof ethhdr)
 |                       | | |
 |,-Dest.--. ,--Src.---. | | |
 |  6 bytes| | 6 bytes | | | |
 v         | |         | | | |
 0         | v       1 | v | v           2
 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5
     ^     | ^         | ^ |
     |     | |         | | |
     |     | |         | `T' <---- 2 bytes for Type
     |     | |         |
     |     | '---SNAP--' <-------- 6 bytes for SNAP
     |     |
     `-IV--' <-------------------- 4 bytes for IV (WEP)

      SNAP HEADER
```
# mbuf #

```
struct mbuf {
        struct  m_hdr m_hdr;
        union {
                struct {
                        struct  pkthdr MH_pkthdr;       /* M_PKTHDR set */
                        union {
                                struct  m_ext MH_ext;   /* M_EXT set */
                                char    MH_databuf[MHLEN];
                        } MH_dat;
                } MH;
                char    M_databuf[MLEN];                /* !M_PKTHDR, !M_EXT */
        } M_dat;
};

struct m_ext {
        caddr_t ext_buf;                /* start of buffer */
        void    (*ext_free)(caddr_t , u_int, caddr_t);  /* free routine if not the usual */        u_int   ext_size;               /* size of buffer, for ext_free */
        caddr_t ext_arg;                /* additional ext_free argument */
        struct  ext_refsq {             /* references held */
                struct ext_refsq *forward, *backward;
        } ext_refs;
};
/* header at beginning of each mbuf: */
struct m_hdr {
        struct  mbuf *mh_next;          /* next buffer in chain */
        struct  mbuf *mh_nextpkt;       /* next chain in queue/record */
        long    mh_len;                 /* amount of data in this mbuf */
        caddr_t mh_data;                /* location of data */
        short   mh_type;                /* type of data in this mbuf */
        short   mh_flags;               /* flags; see below */
};
struct m_tag {
        SLIST_ENTRY(m_tag)      m_tag_link;     /* List of packet tags */
        u_int16_t                       m_tag_type;     /* Module specific type */
        u_int16_t                       m_tag_len;      /* Length of data */
        u_int32_t                       m_tag_id;       /* Module ID */
};
struct  pkthdr {
        int     len;                    /* total packet length */
        struct  ifnet *rcvif;           /* rcv interface */

        /* variables for ip and tcp reassembly */
        void    *header;                /* pointer to packet header */
        /* variables for hardware checksum */
#ifdef KERNEL_PRIVATE
        /* Note: csum_flags is used for hardware checksum and VLAN */
#endif KERNEL_PRIVATE
        int     csum_flags;             /* flags regarding checksum */       
        int     csum_data;              /* data field used by csum routines */
        struct mbuf *aux;               /* extra data buffer; ipsec/others */
#ifdef KERNEL_PRIVATE
        u_short vlan_tag;               /* VLAN tag, host byte order */
        u_short socket_id;              /* socket id */
#else KERNEL_PRIVATE
        u_int   reserved1;              /* for future use */
#endif KERNEL_PRIVATE
        SLIST_HEAD(packet_tags, m_tag) tags; /* list of packet tags */
};
```