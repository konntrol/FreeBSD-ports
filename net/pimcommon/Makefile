PORTNAME=	pimcommon
DISTVERSION=	${KDE_APPLICATIONS_VERSION}
PORTREVISION=	1
CATEGORIES=	net kde kde-applications

MAINTAINER=	kde@FreeBSD.org
COMMENT=	Common libriares for KDEPim

LICENSE=	LGPL21

BUILD_DEPENDS=	${LOCALBASE}/include/boost/range/algorithm.hpp:devel/boost-libs

USES=		cmake compiler:c++11-lib gettext grantlee:5 kde:5 qt:5 tar:xz
USE_KDE=	archive attica auth codecs completion config configwidgets \
		coreaddons dbusaddons emoticons i18n init iconthemes itemmodels \
		jobwidgets kio newstuff service sonnet textwidgets \
		wallet widgetsaddons xmlgui \
		ecm_build
# pim components
USE_KDE+=	akonadi akonadicontacts contacts imap libkdepim mime \
		pimtextedit purpose
USE_QT=		concurrent core dbus designer gui network printsupport script testlib \
		uiplugin uitools webkit widgets xml \
		buildtools_build qmake_build
USE_LDCONFIG=	yes

DESCR=		${.CURDIR:H:H}/deskutils/kdepim/pkg-descr


OPTIONS_DEFINE=	DOCS

.include <bsd.port.mk>
