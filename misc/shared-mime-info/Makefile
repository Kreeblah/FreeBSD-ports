# Created by: olgeni@FreeBSD.org
# $FreeBSD$

PORTNAME=	shared-mime-info
PORTVERSION=	1.8
CATEGORIES=	misc gnome
MASTER_SITES=	http://people.freedesktop.org/~hadess/

MAINTAINER=	gnome@FreeBSD.org
COMMENT=	MIME types database from the freedesktop.org project

GNU_CONFIGURE=	yes
CONFIGURE_ARGS=	--disable-update-mimedb
USES=		pathfix pkgconfig gettext gmake tar:xz
USE_GNOME=	glib20 libxml2 intltool intlhack
CPPFLAGS+=	-I${LOCALBASE}/include
LDFLAGS+=	-L${LOCALBASE}/lib
MAKE_JOBS_UNSAFE=	yes

SUB_FILES=	pkg-install
SUB_LIST=	MIMEDIRS="${MIMEDIRS:O:u}"

MIMEDIRS=	${LOCALBASE}/share/mime \
		${PREFIX}/share/mime
MIMESUBDIRS=	application audio image inode message model multipart \
		packages text video x-epoc x-content

post-patch:
	@${REINPLACE_CMD} -e 's|/usr/local|${LOCALBASE}|g' \
		${WRKSRC}/update-mime-database.c

.include <bsd.port.mk>
