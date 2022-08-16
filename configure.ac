#   Copyright (C) 2022  Libre MATE
#
# This library is free software; you can redistribute it and/or
# modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation; either
# version 2.1 of the License, or (at your option) any later version.
#
# This library is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
# Lesser General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public
# License along with this library; if not, write to the Free Software
# Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301  USA

AC_INIT([mate-submodules],
        [1.24.0],
        [https://github.com/Libre-MATE/mate-submodules/issues],
        [mate-submodules],
        [https://github.com/Libre-MATE/mate-submodules/])
AC_PREREQ(2.61)
AM_INIT_AUTOMAKE([1.11 foreign dist-xz no-dist-gzip silent-rules check-news])
AC_CONFIG_SRCDIR([config.h.in])
AC_CONFIG_HEADER([config.h])
AC_CONFIG_MACRO_DIR([m4])

MATE_COMMON_INIT
MATE_DEBUG_CHECK([no])
MATE_COMPILE_WARNINGS

AC_PROG_CC
LT_INIT([disable-static])
PKG_PROG_PKG_CONFIG

dnl ==========================================================================
dnl
dnl If you add a version number here, you *must* add an AC_SUBST line for
dnl it too, or it will never make it into the spec file!
dnl
dnl ==========================================================================

GLIB_REQUIRED=2.50.0
GTK_REQUIRED=3.22.0
ICE_REQUIRED=1.0.0
SM_REQUIRED=1.0.0

AC_SUBST(GLIB_REQUIRED)
AC_SUBST(GTK_REQUIRED)
AC_SUBST(ICE_REQUIRED)
AC_SUBST(SM_REQUIRED)

dnl ===========================================================================

PKG_CHECK_MODULES(LIBEGG, [glib-2.0 >= $GLIB_REQUIRED
                           gtk+-3.0 >= $GTK_REQUIRED
                           sm >= $SM_REQUIRED
                           gthread-2.0 >= $GLIB_REQUIRED
                           ice >= $ICE_REQUIRED])
AC_SUBST([LIBEGG_CFLAGS])
AC_SUBST([LIBEGG_LIBS])

dnl ******************************

AC_CONFIG_FILES([
Makefile
libegg/Makefile
])
AC_OUTPUT

echo "
Configuration:

	Source code location:   ${srcdir}
	Compiler:               ${CC}
	Compiler flags:         ${CFLAGS}
	Warning flags:          ${WARN_CFLAGS}
	Linker flags:           ${LDFLAGS}
"
