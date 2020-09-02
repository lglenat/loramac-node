if(${CONFIG_HAS_SEMTECH_LORAMAC})

set(ZEPHYR_CURRENT_LIBRARY loramac-node)

zephyr_library_include_directories(../src/boards)
zephyr_library_include_directories(../src/mac)
zephyr_library_include_directories(../src/radio)
zephyr_library_include_directories(../src/system)
zephyr_library_include_directories(../src/radio/lr1110)
zephyr_library_include_directories(../src/radio/lr1110/lr1110_driver)
zephyr_library_include_directories(../src/radio/lr1110/lr1110_driver/src)
zephyr_library_include_directories(../src/peripherals/lr1110-se)
zephyr_library_include_directories(../src/peripherals/soft-se)

zephyr_library_sources_ifdef(CONFIG_HAS_SEMTECH_LORAMAC ../src/mac/LoRaMacAdr.c)
zephyr_library_sources_ifdef(CONFIG_HAS_SEMTECH_LORAMAC ../src/mac/LoRaMac.c)
zephyr_library_sources_ifdef(CONFIG_HAS_SEMTECH_LORAMAC ../src/mac/LoRaMacClassB.c)
zephyr_library_sources_ifdef(CONFIG_HAS_SEMTECH_LORAMAC ../src/mac/LoRaMacCommands.c)
zephyr_library_sources_ifdef(CONFIG_HAS_SEMTECH_LORAMAC ../src/mac/LoRaMacConfirmQueue.c)
zephyr_library_sources_ifdef(CONFIG_HAS_SEMTECH_LORAMAC ../src/mac/LoRaMacCrypto.c)
zephyr_library_sources_ifdef(CONFIG_HAS_SEMTECH_LORAMAC ../src/mac/LoRaMacParser.c)
zephyr_library_sources_ifdef(CONFIG_HAS_SEMTECH_LORAMAC ../src/mac/LoRaMacSerializer.c)

zephyr_library_sources_ifdef(CONFIG_HAS_SEMTECH_LORAMAC ../src/peripherals/soft-se/aes.c)
zephyr_library_sources_ifdef(CONFIG_HAS_SEMTECH_LORAMAC ../src/peripherals/soft-se/cmac.c)
zephyr_library_sources_ifdef(CONFIG_HAS_SEMTECH_SX1276 ../src/peripherals/soft-se/soft-se.c)

zephyr_library_sources_ifdef(CONFIG_HAS_SEMTECH_SX1276 ../src/radio/sx1276/sx1276.c)

zephyr_library_sources_ifdef(CONFIG_HAS_SEMTECH_SX126X ../src/radio/sx126x/sx126x.c)
zephyr_library_sources_ifdef(CONFIG_HAS_SEMTECH_SX126X ../src/radio/sx126x/radio.c)

zephyr_library_sources_ifdef(CONFIG_HAS_SEMTECH_LR1110 ../src/radio/lr1110/radio.c)
zephyr_library_sources_ifdef(CONFIG_HAS_SEMTECH_LR1110 ../src/radio/lr1110/lr1110_driver/src/lr1110_bootloader.c)
zephyr_library_sources_ifdef(CONFIG_HAS_SEMTECH_LR1110 ../src/radio/lr1110/lr1110_driver/src/lr1110_driver_version.c)
zephyr_library_sources_ifdef(CONFIG_HAS_SEMTECH_LR1110 ../src/radio/lr1110/lr1110_driver/src/lr1110_gnss.c)
zephyr_library_sources_ifdef(CONFIG_HAS_SEMTECH_LR1110 ../src/radio/lr1110/lr1110_driver/src/lr1110_radio.c)
zephyr_library_sources_ifdef(CONFIG_HAS_SEMTECH_LR1110 ../src/radio/lr1110/lr1110_driver/src/lr1110_regmem.c)
zephyr_library_sources_ifdef(CONFIG_HAS_SEMTECH_LR1110 ../src/radio/lr1110/lr1110_driver/src/lr1110_system.c)
zephyr_library_sources_ifdef(CONFIG_HAS_SEMTECH_LR1110 ../src/radio/lr1110/lr1110_driver/src/lr1110_wifi.c)

zephyr_library_sources_ifdef(CONFIG_HAS_LR1110_SECURE_ELEMENT ../src/radio/lr1110/lr1110_driver/src/lr1110_crypto_engine.c)
zephyr_library_sources_ifdef(CONFIG_HAS_LR1110_SECURE_ELEMENT ../src/peripherals/lr1110-se/lr1110-se.c)
zephyr_library_sources_ifdef(CONFIG_HAS_LR1110_SECURE_ELEMENT ../src/peripherals/lr1110-se/lr1110-se-hal.c)

zephyr_library_sources_ifdef(CONFIG_HAS_LR1110_SOFT_SE ../src/peripherals/soft-se/soft-se.c)
zephyr_library_sources_ifdef(CONFIG_HAS_LR1110_SOFT_SE ../src/peripherals/soft-se/aes.c)
zephyr_library_sources_ifdef(CONFIG_HAS_LR1110_SOFT_SE ../src/peripherals/soft-se/cmac.c)
zephyr_library_sources_ifdef(CONFIG_HAS_LR1110_SOFT_SE ../src/peripherals/soft-se/soft-se-hal.c)

zephyr_library_sources_ifdef(CONFIG_HAS_SEMTECH_LORAMAC ../src/system/timer.c)
zephyr_library_sources_ifdef(CONFIG_HAS_SEMTECH_LORAMAC ../src/system/delay.c)
zephyr_library_sources_ifdef(CONFIG_HAS_SEMTECH_LORAMAC ../src/system/systime.c)

zephyr_library_sources_ifdef(CONFIG_HAS_SEMTECH_LORAMAC ../src/boards/mcu/utilities.c)

zephyr_library_sources_ifdef(CONFIG_HAS_SEMTECH_LORAMAC ../src/mac/region/Region.c)
zephyr_library_sources_ifdef(CONFIG_HAS_SEMTECH_LORAMAC ../src/mac/region/RegionCommon.c)
zephyr_library_sources_ifdef(CONFIG_HAS_LORAMAC_REGION_EU868 ../src/mac/region/RegionEU868.c)
zephyr_library_compile_definitions_ifdef(CONFIG_HAS_LORAMAC_REGION_EU868 REGION_EU868="ON")
zephyr_library_sources_ifdef(CONFIG_HAS_LORAMAC_REGION_US915 ../src/mac/region/RegionUS915.c)
zephyr_library_compile_definitions_ifdef(CONFIG_HAS_LORAMAC_REGION_US915 REGION_US915="ON")

zephyr_library_compile_definitions_ifdef(CONFIG_HAS_LORAMAC_ACTIVE_REGION_US915 ACTIVE_REGION="LORAMAC_REGION_EU868")

zephyr_library_compile_definitions_ifdef(CONFIG_HAS_LR1110_SECURE_ELEMENT SECURE_ELEMENT_PRE_PROVISIONED="ON")
zephyr_library_compile_definitions_ifdef(CONFIG_HAS_LR1110_SECURE_ELEMENT SECURE_ELEMENT="LR1110_SE")

zephyr_library_compile_definitions_ifdef(CONFIG_HAS_LR1110_SOFT_SE SECURE_ELEMENT="LR1110_SE")

endif()
