
# File: main/CMakeLists.txt
# LilyGO THMI IDF Template Project
cmake_minimum_required(VERSION 3.16)

# Set usual component variables
set(
    app_sources
    "main.c"
)

set(
    app_include_dirs
    "."
    ""
)

set(
    app_requires
    driver
    esp_psram
    fatfs
    spi_flash
    esp_driver_usb_serial_jtag
    esp_system
    heap
    esp_common
    esp_hw_support
)

set(
    app_priv_requires
    ${app_requires}
    esp_bootloader_format
    nvs_flash
    esp_wifi
    console
    esp_rom
)

# Set my components
# These are components that are not part of the IDF 
# but are used in this project.
# Put this components in /lib after set 
# set(EXTRA_COMPONENT_DIRS lib) in root/CMakeLists.txt
set(
    my_components_add
	#component here
)

idf_component_register(
    SRCS
    ${app_sources}
    INCLUDE_DIRS
    ${app_include_dirs}
    REQUIRES
    ${app_requires}
    ${my_components_add}
    PRIV_REQUIRES
    ${app_priv_requires}
    WHOLE_ARCHIVE
)


# Note: you must have a partition named the first argument (here it's "littlefs")
# in your partition table csv file.
# littlefs_create_partition_image(littlefs littlefs_data FLASH_IN_PROJECT)
# spiffs_create_partition_image(spiffs spiffs_data FLASH_IN_PROJECT)
