##########################################################################################
##                                                                                      ##
##                                 libgost15 selftests                                  ##
##                                                                                      ##
##########################################################################################

function(add_test_executable test_name)
    add_executable(${test_name} ${ARGN})
    set_target_properties(${test_name} PROPERTIES
            C_EXTENSIONS OFF
            C_STANDARD 99
            C_STANDARD_REQUIRED ON)
    target_link_libraries(${test_name} PUBLIC lg15)
    add_test(${test_name} ${test_name})
endfunction(add_test_executable)

add_test_executable(KeyScheduleTest src/schedule.c)
add_test_executable(BlockEncryptionTest src/encryption.c)
add_test_executable(BlockDecryptionTest src/decryption.c)
