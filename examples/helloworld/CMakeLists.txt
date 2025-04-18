add_executable(hal_st.helloworld_nucleo64 Main.cpp)
emil_build_for(hal_st.helloworld_nucleo64
    TARGET_MCU stm32g474
    TARGET_MCU stm32wb55
    TARGET_MCU stm32wba52
    TARGET_MCU stm32wba65
    PREREQUISITE_BOOL HALST_BUILD_EXAMPLES
)

target_compile_definitions(hal_st.helloworld_nucleo64 PUBLIC
    $<$<STREQUAL:${TARGET_MCU},stm32wba52>:NUCLEO=Nucleo64WBAUi>
    $<$<STREQUAL:${TARGET_MCU},stm32wba65>:NUCLEO=Nucleo64WBA6Ui>
    $<$<STREQUAL:${TARGET_MCU},stm32wb55>:NUCLEO=Nucleo64WBUi>
    $<$<STREQUAL:${TARGET_MCU},stm32g474>:NUCLEO=Nucleo64WBUi>
)

target_link_libraries(hal_st.helloworld_nucleo64 PRIVATE
    services.util
    hal_st.instantiations
)

halst_target_default_linker_scripts(hal_st.helloworld_nucleo64)
halst_target_default_init(hal_st.helloworld_nucleo64)

emil_generate_artifacts(TARGET hal_st.helloworld_nucleo64 LST MAP BIN HEX)

######################################################################

add_executable(hal_st.helloworld_nucleo144 Main.cpp)
emil_build_for(hal_st.helloworld_nucleo144
    TARGET_MCU stm32f767
    TARGET_MCU stm32h563
    PREREQUISITE_BOOL HALST_BUILD_EXAMPLES
)

target_compile_definitions(hal_st.helloworld_nucleo144 PUBLIC
    NUCLEO=Nucleo144Ui
)

target_link_libraries(hal_st.helloworld_nucleo144 PRIVATE
    services.util
    hal_st.instantiations
)

halst_target_default_linker_scripts(hal_st.helloworld_nucleo144)
halst_target_default_init(hal_st.helloworld_nucleo144)

emil_generate_artifacts(TARGET hal_st.helloworld_nucleo144 LST MAP BIN HEX)
