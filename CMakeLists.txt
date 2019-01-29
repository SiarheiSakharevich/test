cmake_minimum_required(VERSION 3.5.2)

include("$ENV{SBISPlatformSDK_19300}/tools/cmake_support/sbis.cmake")

sbis_create_project("sbis-disk-edo-service" library DEPENDS boost_headers)

sbis_add_dependency("sbis-disk-objects-db" "../sbis-disk-objects-db")
sbis_add_dependency("sbis-disk-bl" "../sbis-disk-bl")
sbis_add_dependency("sbis-disk-utils" "../sbis-disk-utils")
sbis_add_dependency("sbis-disk-base" "../../sbis-disk-client/sbis-disk-base")
sbis_add_dependency("sbis-disk-base-utils" "../../sbis-disk-client/sbis-disk-base-utils")

file(GLOB_RECURSE sources_list "implementation/*.cpp")
file(GLOB_RECURSE headers_list "implementation/*.{h,hpp}" "sbis-disk-edo-service/*.{h,hpp}")

sbis_set_sources(${sources_list})
sbis_set_headers(${headers_list})

sbis_declare_export_macro(SBIS_DISK_MAINSERVICE_EXPORTS)

sbis_add_sdk_dependency("sbis-lib300")
sbis_add_sdk_dependency("sbis-dbi300")
sbis_add_sdk_dependency("sbis-bl-service300")
sbis_add_sdk_dependency("sbis-bl-core300")
sbis_add_sdk_dependency("sbis-rpc300")
sbis_add_sdk_dependency("sbis-event-subscription300")
sbis_add_sdk_dependency("sbis-email300")
sbis_add_sdk_dependency("sbis-rpc-client300")

sbis_copy_binary_to("../www/service/Модули/СбисДиск - ЭДО")

sbis_apply_settings()
