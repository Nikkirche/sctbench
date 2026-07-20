set(SCT_OK_SOURCE_TARGET_LIST
        account_ok.c
        arithmetic_prog_ok.c
        circular_buffer_ok.c
        fanger01_ok.c
        fsbench_ok.c
        indexer_ok.c
        lazy01_ok.c
        micro_2_ok.c
        micro_3_ok.c
        micro_10_ok.c
        phase01_ok.c
        queue_ok.c
        stack_ok.c
        stateful01_ok.c
        stateful06_ok.c
        stateful20_ok.c
        sync01_ok.c
        sync02_ok.c
)

set(SCT_BAD_SOURCE_TARGET_LIST
        account_bad.c
        arithmetic_prog_bad.c
        bluetooth_driver_bad.c
        carter01_bad.c
        circular_buffer_bad.c
        deadlock01_bad.c
        fsbench_bad.c
        lazy01_bad.c
        phase01_bad.c
        queue_bad.c
        reorder_3_bad.c
        reorder_4_bad.c
        reorder_5_bad.c
        reorder_10_bad.c
        reorder_20_bad.c
        stack_bad.c
        sync01_bad.c
        sync02_bad.c
        token_ring_bad.c
        twostage_100_bad.c
        twostage_bad.c
        wronglock_3_bad.c
        wronglock_bad.c
)

foreach (source_name ${SCT_OK_SOURCE_TARGET_LIST})
    get_filename_component(target ${source_name} NAME_WE)
    verify_external_target(${target})
    add_external_integration_test("${target}" "sct" FALSE
            ${target}
    )
endforeach (source_name ${SCT_OK_SOURCE_TARGET_LIST})

foreach (source_name ${SCT_BAD_SOURCE_TARGET_LIST})
    get_filename_component(target ${source_name} NAME_WE)
    verify_external_target(${target})
    add_external_integration_test("${target}" "sct" TRUE
            ${target}
    )
endforeach (source_name ${SCT_BAD_SOURCE_TARGET_LIST})

