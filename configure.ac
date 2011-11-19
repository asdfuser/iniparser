AC_PREREW(2.53)
AC_INIT([iniparser], [3.0], [Nicolas Devillard])
AM_INIT_AUTOMAKE()

AC_PROG_MAKE_SET
AC_PROG_CC
AC_PROG_INSTALL
LT_INIT
AC_PROG_LIBTOOL
AM_PROG_CC_C_O

dnl Check for doxygen
AC_ARG_ENABLE([doc],
	AS_HELP_STRING([--disable-doc], [Do not build API documentation]),
	[ac_enable_doc=$enableval], [ac_enable_doc=auto])

if test "x$ac_enable_doc" != "xno"; then
	AC_CHECK_PROG(HAVE_DOXYGEN, doxygen, true, false)

	if test "x$HAVE_DOXYGEN" = "xfalse" -a "x$ac_enable_doc" = "xyes"; then
		AC_MSG_ERROR([*** API documentation explicitly requested but Doxygen not found])
	fi
else
	HAVE_DOXYGEN=false
fi
AM_CONDITIONAL(HAVE_DOXYGEN,$HAVE_DOXYGEN)
if test $HAVE_DOXYGEN = "false"; then
        AC_MSG_WARN([*** doxygen not found, API documentation will not be built])
fi

AC_OUTPUT([
libiniparser.pc
Makefile
src/Makefile
doc/Makefile
doc/Doxyfile
test/Makefile])
