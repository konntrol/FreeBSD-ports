# Created by: Emanuel Haupt <ehaupt@FreeBSD.org>

PORTNAME=	websockets
PORTVERSION=	9.1
CATEGORIES=	devel python
MASTER_SITES=	CHEESESHOP
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	ehaupt@FreeBSD.org
COMMENT=	Implementation of the WebSocket Protocol (RFC 6455 and 7692)

LICENSE=	BSD3CLAUSE

USES=		python:3.6+
USE_PYTHON=	autoplist distutils

post-install:
	@${STRIP_CMD} ${STAGEDIR}${PYTHON_SITELIBDIR}/websockets/speedups*.so

.include <bsd.port.mk>
