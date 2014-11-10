#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.69])
AC_INIT([stlink-trace],[1.0])
AC_CONFIG_AUX_DIR(build-aux)
AC_REQUIRE_AUX_FILE(config.guess)
AC_CANONICAL_BUILD
AC_CANONICAL_HOST
AC_CANONICAL_TARGET
AC_CONFIG_MACRO_DIR(m4)
AM_INIT_AUTOMAKE([-Wall -Werror foreign])
AC_CONFIG_SRCDIR([stlink-trace.c])


# Checks for programs.
AC_PROG_CC
AC_PROG_CC_C99

# Checks for libraries.
AX_WITH_CURSES

# Checks for header files.
AC_CHECK_HEADERS([stdlib.h unistd.h])

# Checks for libraries.
PKG_CHECK_MODULES(USB, libusb-1.0 >= 1.0.0,,
	AC_MSG_ERROR([*** Required libusb-1.0 >= 1.0.0 not installed ***]))
LIBS="$LIBS $USB_LIBS"
CFLAGS="$CFLAGS $USB_CFLAGS"

case "${host}" in
	*-mingw*)
		AC_DEFINE([__USE_MINGW_ANSI_STDIO], [1],
			  [C99 compliant printf function])
        ;;
	*)
esac

# Checks for library functions.
AC_CHECK_FUNCS([gettimeofday])

# Checks for typedefs, structures, and compiler characteristics.
AC_TYPE_SIZE_T
AC_TYPE_SSIZE_T
AC_TYPE_UINT32_T
AC_TYPE_UINT8_T

AC_CONFIG_HEADERS([config.h])
AC_CONFIG_FILES([Makefile])
AC_OUTPUT
