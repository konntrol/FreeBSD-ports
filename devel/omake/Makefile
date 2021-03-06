# Created by: Stanislav Sedov <ssedov@mbsd.msk.ru>

PORTNAME=	omake
DISTVERSION=	0.9.8.6-0.rc1
PORTREVISION=	4
CATEGORIES=	devel
MASTER_SITES=	http://pkgs.fedoraproject.org/repo/pkgs/ocaml-omake/omake-0.9.8.6-0.rc1.tar.gz/fe39a476ef4e33b7ba2ca77a6bcaded2/ \
		http://download.camlcity.org/download/

MAINTAINER=	ports@FreeBSD.org
COMMENT=	Flexible build system

LICENSE=	GPLv2
LICENSE_FILE=	${WRKSRC}/LICENSE

WRKSRC=		${WRKDIR}/${PORTNAME}-${DISTVERSION:C|-.*||}
USE_OCAML=	yes
NO_OCAML_RUNDEPENDS=yes
USES=		ncurses readline
MAKE_ENV=	INSTALL_ROOT=${STAGEDIR}
MAKE_JOBS_UNSAFE=	yes

INFO=		omake-doc

OPTIONS_DEFINE=	DOCS

.include <bsd.port.pre.mk>

post-patch:
#
# Dirty hack for PREFIX safety
#
	@${REINPLACE_CMD} -E -e \
		's|(getenv[[:space:]]+)LIBDIR|\1PREFLIBDIR|' ${WRKSRC}/mk/defaults

#
# Permissions safety
#
.for f in OMakefile doc/OMakefile src/main/OMakefile
	@${REINPLACE_CMD} -e \
		's|cp -f -m 444|$$(BSD_INSTALL_DATA)| ; \
		 s|cp -f -m 555|$$(BSD_INSTALL_PROGRAM)|' ${WRKSRC}/${f}
.endfor
	@${REINPLACE_CMD} -e 's| -j2 | |' ${WRKSRC}/Makefile
.if ${NCURSESBASE} == "/usr"
.for f in lib/configure/ncurses.om src/libmojave-external/cutil/lm_terminfo.c
	@${REINPLACE_CMD} -E -e 's|ncurses/(term\.h)|\1|' ${WRKSRC}/${f}
.endfor
.endif

do-test:
	@cd ${WRKSRC}; ${SETENV} ${MAKE_ENV} ${MAKE_ARGS} boot/omake check
	@${FIND} -ds ${WRKSRC}/test -type f -name 'result.log' -print0 | \
		${XARGS} -0tI @ ${CAT} @

bench: build
	@cd ${WRKSRC}; ${SETENV} ${MAKE_ENV} ${MAKE_ARGS} boot/omake bench

post-install:
	@(cd ${WRKSRC}/doc/info && ${INSTALL_DATA} omake-doc.info \
		${STAGEDIR}${PREFIX}/${INFO_PATH})
	@(cd ${WRKSRC}/doc/info && ${INSTALL_DATA} omake-doc.info-* \
		${STAGEDIR}${PREFIX}/${INFO_PATH})

post-install-DOCS-on:
	@${MKDIR} ${STAGEDIR}${DOCSDIR}
	@(cd ${WRKSRC}/doc/html && ${COPYTREE_SHARE} . ${STAGEDIR}${DOCSDIR})

.include <bsd.port.post.mk>
