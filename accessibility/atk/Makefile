# Created by: Maxim Sobolev <sobomax@FreeBSD.org>

PORTNAME=	atk
PORTVERSION=	2.36.0
PORTREVISION?=	0
CATEGORIES=	accessibility devel
MASTER_SITES=	GNOME
DIST_SUBDIR=	gnome

MAINTAINER=	desktop@FreeBSD.org
COMMENT=	GNOME accessibility toolkit (ATK)

LICENSE=	LGPL20+
LICENSE_FILE=	${WRKSRC}/COPYING

PORTSCOUT=	limitw:1,even

USE_LDCONFIG=	yes
USES=		gettext gnome localbase meson pkgconfig tar:xz
USE_GNOME=	glib20 introspection:build

.include <bsd.port.mk>
