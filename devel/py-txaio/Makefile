# Created by: Kubilay Kocak <koobs@FreeBSD.org>

PORTNAME=	txaio
PORTVERSION=	18.8.1
CATEGORIES=	devel python
MASTER_SITES=	CHEESESHOP
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

MAINTAINER=	koobs@FreeBSD.org
COMMENT=	Compatibility API between asyncio/Twisted/Trollius

LICENSE=	MIT
LICENSE_FILE=	${WRKSRC}/LICENSE

RUN_DEPENDS=	${PYTHON_PKGNAMEPREFIX}six>0:devel/py-six@${PY_FLAVOR}
TEST_DEPENDS=	${PYTHON_PKGNAMEPREFIX}pytest>=2.6.4:devel/py-pytest@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}mock>=1.3.0:devel/py-mock@${PY_FLAVOR} \
		${PYTHON_PKGNAMEPREFIX}twisted>=12.1.0:devel/py-twisted@${PY_FLAVOR}

USES=		python:3.6+
USE_PYTHON=	autoplist distutils

PATCH_SITES=	https://github.com/crossbario/${PORTNAME}/commit/
PATCHFILES=	9217f054b7eccc120f84e01995479125e07de59a.patch:-p1

NO_ARCH=	yes

do-test:
	@cd ${WRKSRC} && ${PYTHON_CMD} -m pytest -v -rs

.include <bsd.port.mk>
