AC_INIT([MatrixExtra], 0.1.9)

HAS_LD=`${R_HOME}/bin${R_ARCH_BIN}/Rscript -e "cat(unname(as.integer(capabilities('long.double'))))"`
AC_SUBST(HAS_LD)

FLOAT_LIBS=`${R_HOME}/bin${R_ARCH_BIN}/Rscript -e "float:::ldflags(static=Sys.info()[['sysname']] == 'Darwin')"`
AC_SUBST(FLOAT_LIBS)

AC_LANG(C++)
AC_COMPILE_IFELSE(
    [AC_LANG_PROGRAM([[]], [[double *__restrict x;]])],
    [SUPPORTS_RESTRICT="-DSUPPORTS_RESTRICT=1"],
    [SUPPORTS_RESTRICT=""]
)
AC_SUBST(SUPPORTS_RESTRICT)

AC_LANG(C++)
OLD_CXXFLAGS="$CXXFLAGS"
CXXFLAGS="$CXXFLAGS -fno-math-errno"
AC_COMPILE_IFELSE(
    [AC_LANG_PROGRAM([[]])],
    [FNE_FLAG="-fno-math-errno"],
    [FNE_FLAG=""]
)
CXXFLAGS="$OLD_CXXFLAGS"
AC_SUBST(FNE_FLAG)

OLD_CXXFLAGS="$CXXFLAGS"
CXXFLAGS="$CXXFLAGS -fno-trapping-math"
AC_COMPILE_IFELSE(
    [AC_LANG_PROGRAM([[]])],
    [FNTP_FLAG="-fno-trapping-math"],
    [FNTP_FLAG=""]
)
CXXFLAGS="$OLD_CXXFLAGS"
AC_SUBST(FNTP_FLAG)

AC_CONFIG_FILES([src/Makevars])
AC_OUTPUT 
