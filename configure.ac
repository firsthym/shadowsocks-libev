#                                               -*- Autoconf -*-
# Process this file with autoconf to produce a configure script.

AC_PREREQ([2.67])
AC_INIT([shadowsocks], [1.3], [max.c.lv@gmail.com])
AC_CONFIG_SRCDIR([src/encrypt.c])
AC_CONFIG_HEADERS([config.h])

AM_INIT_AUTOMAKE([foreign -Wall -Werror])
AM_PROG_AR

# Checks for programs.
AC_PROG_CC
AC_PROG_INSTALL
AC_PROG_LIBTOOL
AC_PROG_LN_S
AC_PROG_MAKE_SET

m4_include([libev/libev.m4])

# Checks for host.

AC_MSG_CHECKING(for what kind of host)
case $host in
  *-linux*)
    os_support=linux
    AC_MSG_RESULT(Linux)
    ;;
  *)
    AC_MSG_RESULT(transparent proxy does not support for $host)
    ;;
esac

AM_CONDITIONAL(BUILD_REDIRECTOR, test "$os_support" = "linux")

# Checks for header files.
AC_CHECK_HEADERS([stdint.h inttypes.h arpa/inet.h fcntl.h langinfo.h locale.h netdb.h netinet/in.h stdlib.h string.h strings.h sys/socket.h unistd.h net/if.h sys/ioctl.h])

AC_C_BIGENDIAN

# Checks for typedefs, structures, and compiler characteristics.
AC_C_INLINE
AC_TYPE_SSIZE_T

dnl Checks for header files.
AC_HEADER_ASSERT
AC_HEADER_STDC
AC_HEADER_SYS_WAIT

dnl Checks for typedefs, structures, and compiler characteristics.
AC_C_CONST
AC_TYPE_PID_T
AC_TYPE_SIZE_T
AC_TYPE_SSIZE_T
AC_TYPE_UINT16_T
AC_TYPE_UINT8_T
AC_HEADER_TIME

dnl Checks for library functions.
AC_FUNC_FORK
AC_FUNC_MALLOC
AC_FUNC_SELECT_ARGTYPES
AC_TYPE_SIGNAL
AC_CHECK_FUNCS([memset select strndup setresuid setreuid strerror])

AC_SYS_LARGEFILE

AC_CHECK_LIB(socket, connect)

# Checks for library functions.
AC_CHECK_FUNCS([malloc memset socket])

ACX_PTHREAD

AC_CONFIG_MACRO_DIR([m4])

AC_CONFIG_FILES([Makefile
                 libasyncns/Makefile
                 libev/Makefile
                 src/Makefile])
AC_OUTPUT
