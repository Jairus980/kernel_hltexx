CFLAGS_scm.o :=$(call as-instr,.arch_extension sec,-DREQUIRES_SEC=1)

obj-y += io.o dma.o memory.o
ifndef CONFIG_ARM_ARCH_TIMER
obj-y += timer.o
endif
obj-y += clock.o clock-voter.o clock-dummy.o clock-generic.o
obj-y += modem_notifier.o
obj-$(CONFIG_USE_OF) += board-dt.o
obj-$(CONFIG_DEBUG_FS) += nohlt.o clock-debug.o
obj-$(CONFIG_KEXEC) += msm_kexec.o

obj-$(CONFIG_MSM_PROC_COMM) += proc_comm.o clock-pcom.o vreg.o mpp.o
ifdef CONFIG_MSM_PROC_COMM
	obj-$(CONFIG_REGULATOR) += footswitch-pcom.o
	obj-$(CONFIG_DEBUG_FS) += pmic_debugfs.o
endif

obj-y += acpuclock.o
obj-$(CONFIG_HW_PERF_EVENTS) += perf_trace_counters.o
obj-$(CONFIG_ARCH_MSM_KRAIT) += clock-krait.o
ifndef CONFIG_OF
obj-$(CONFIG_HW_PERF_EVENTS) += pmu.o
endif
obj-$(CONFIG_ARCH_MSM_KRAIT) += msm-krait-l2-accessors.o perf_event_msm_krait_l2.o krait-scm.o
ifdef CONFIG_HW_PERF_EVENTS
	obj-$(CONFIG_DEBUG_FS) += perf_debug.o
endif

obj-$(CONFIG_MSM_VIC) += irq-vic.o

obj-$(CONFIG_SMP) += headsmp.o platsmp.o
obj-$(CONFIG_HOTPLUG_CPU) += hotplug.o

obj-$(CONFIG_MSM_AVS_HW) += avs.o
obj-$(CONFIG_CPU_V7) += idle-v7.o
obj-$(CONFIG_MSM_JTAG) += jtag-fuse.o jtag.o
obj-$(CONFIG_MSM_JTAG_MM) +=  jtag-fuse.o jtag-mm.o

msm-etm-objs := etm.o
obj-$(CONFIG_MSM_ETM) += msm-etm.o

quiet_cmd_mkrpcsym = MKCAP   $@
      cmd_mkrpcsym = $(PERL) $(srctree)/$(src)/mkrpcsym.pl $< $@

target += smd_rpc_sym.c
$(obj)/smd_rpc_sym.c: $(src)/smd_rpc_sym $(src)/mkrpcsym.pl
	$(call if_changed,mkrpcsym)

obj-$(CONFIG_MSM_SMD) += smd.o smd_debug.o remote_spinlock.o smd_private.o smem.o smd_init_dt.o smd_init_plat.o
obj-$(CONFIG_MSM_SMP2P) += smp2p.o smp2p_debug.o smp2p_gpio.o
obj-$(CONFIG_MSM_SMP2P_TEST) += smp2p_loopback.o smp2p_test.o smp2p_gpio_test.o smp2p_spinlock_test.o
obj-$(CONFIG_MSM_SCM) += scm.o scm-boot.o
obj-$(CONFIG_MSM_XPU_ERR_FATAL) += scm-xpu.o
obj-$(CONFIG_MSM_SECURE_IO) += scm-io.o
obj-$(CONFIG_MSM_PIL) += peripheral-loader.o
obj-$(CONFIG_MSM_PIL) += scm-pas.o
obj-$(CONFIG_MSM_PIL_QDSP6V3) += pil-q6v3.o
obj-$(CONFIG_MSM_PIL_LPASS_QDSP6V4) += pil-q6v4.o pil-q6v4-lpass.o
obj-$(CONFIG_MSM_PIL_MODEM_QDSP6V4) += pil-q6v4.o pil-q6v4-mss.o
obj-$(CONFIG_MSM_PIL_LPASS_QDSP6V5) += pil-q6v5.o pil-q6v5-lpass.o
obj-$(CONFIG_MSM_PIL_MSS_QDSP6V5) += pil-q6v5.o pil-msa.o pil-q6v5-mss.o
obj-$(CONFIG_MSM_PIL_RIVA) += pil-riva.o
obj-$(CONFIG_MSM_PIL_TZAPPS) += pil-tzapps.o
obj-$(CONFIG_MSM_PIL_VIDC) += pil-vidc.o
obj-$(CONFIG_MSM_PIL_MODEM) += pil-modem.o
obj-$(CONFIG_MSM_PIL_DSPS) += pil-dsps.o
obj-$(CONFIG_MSM_PIL_GSS) += pil-gss.o
obj-$(CONFIG_MSM_PIL_PRONTO) += pil-pronto.o
obj-$(CONFIG_MSM_PIL_VENUS) += pil-venus.o
obj-$(CONFIG_MSM_FIQ_SUPPORT) += fiq_glue.o
obj-$(CONFIG_MSM_BAM_DMUX) += bam_dmux.o
obj-$(CONFIG_MSM_SMD_LOGGING) += smem_log.o
obj-$(CONFIG_MSM_COMMON_LOG) += common_log.o
obj-$(CONFIG_MSM_IPC_LOGGING) += ipc_logging.o
ifdef CONFIG_DEBUG_FS
	obj-$(CONFIG_MSM_IPC_LOGGING) += ipc_logging_debug.o
endif
obj-y += socinfo.o
obj-$(CONFIG_MSM_SMD_TTY) += smd_tty.o
obj-$(CONFIG_MSM_SMD_QMI) += smd_qmi.o
obj-$(CONFIG_MSM_SMD_PKT) += smd_pkt.o
obj-$(CONFIG_MSM_DSPS) += msm_dsps.o
obj-$(CONFIG_MSM_SMD_NMEA) += smd_nmea.o
obj-$(CONFIG_MSM_RESET_MODEM) += reset_modem.o
obj-$(CONFIG_MSM_IPC_ROUTER_SMD_XPRT) += ipc_router_smd_xprt.o
obj-$(CONFIG_MSM_IPC_ROUTER_HSIC_XPRT) += ipc_router_hsic_xprt.o
obj-$(CONFIG_MSM_ONCRPCROUTER) += smd_rpcrouter.o
obj-$(CONFIG_MSM_ONCRPCROUTER) += smd_rpcrouter_device.o
obj-$(CONFIG_MSM_IPC_ROUTER) += ipc_router.o
obj-$(CONFIG_MSM_IPC_ROUTER)+= ipc_socket.o
obj-$(CONFIG_MSM_IPC_ROUTER_SECURITY)+= msm_ipc_router_security.o
obj-$(CONFIG_MSM_QMI_INTERFACE) += msm_qmi_interface.o
obj-$(CONFIG_MSM_TEST_QMI_CLIENT) += kernel_test_service_v01.o test_qmi_client.o
obj-$(CONFIG_DEBUG_FS) += smd_rpc_sym.o
obj-$(CONFIG_MSM_ONCRPCROUTER) += smd_rpcrouter_servers.o
obj-$(CONFIG_MSM_ONCRPCROUTER) += smd_rpcrouter_clients.o
obj-$(CONFIG_MSM_ONCRPCROUTER) += smd_rpcrouter_xdr.o
obj-$(CONFIG_MSM_ONCRPCROUTER) += rpcrouter_smd_xprt.o
obj-$(CONFIG_MSM_RPC_PING) += ping_mdm_rpc_client.o
obj-$(CONFIG_MSM_RPC_PROC_COMM_TEST) += proc_comm_test.o
obj-$(CONFIG_MSM_RPC_PING) += ping_mdm_rpc_client.o ping_apps_server.o
obj-$(CONFIG_MSM_RPC_OEM_RAPI) += oem_rapi_client.o
obj-$(CONFIG_MSM_RPC_WATCHDOG) += rpc_dog_keepalive.o
obj-$(CONFIG_MSM_RPCSERVER_WATCHDOG) += rpc_server_dog_keepalive.o
obj-$(CONFIG_MSM_RPCSERVER_TIME_REMOTE) += rpc_server_time_remote.o
obj-$(CONFIG_MSM_DALRPC) += dal.o
obj-$(CONFIG_MSM_DALRPC_TEST) += dal_remotetest.o
obj-$(CONFIG_MSM_RPCSERVER_HANDSET) += rpc_server_handset.o
obj-$(CONFIG_MSM_AUDIO_QDSP6) += qdsp6v2/
obj-$(CONFIG_MSM_AUDIO_QDSP6V2) += qdsp6v2/
obj-$(CONFIG_MSM_HW3D) += hw3d.o
obj-$(CONFIG_PM) += pm-boot.o
obj-$(CONFIG_MSM_IDLE_STATS) += pm-stats.o
obj-$(CONFIG_MSM_PM2) += pm2.o
obj-$(CONFIG_MSM_NOPM) += no-pm.o

obj-$(CONFIG_MSM_PCIE) += pcie.o pcie_irq.o

obj-$(CONFIG_MSM_SPM_V1) += spm.o
obj-$(CONFIG_MSM_SPM_V2) += spm-v2.o spm_devices.o

obj-$(CONFIG_MSM_DMA_TEST) += dma_test.o
obj-$(CONFIG_SURF_FFA_GPIO_KEYPAD) += keypad-surf-ffa.o

obj-$(CONFIG_MSM_BOOT_STATS) += boot_stats.o

ifdef CONFIG_MSM_RPM_REGULATOR
	obj-y += rpm-regulator.o
endif

obj-$(CONFIG_MSM_RPM_REGULATOR_SMD) += rpm-regulator-smd.o
obj-$(CONFIG_MSM_SPM_REGULATOR) += spm-regulator.o

ifdef CONFIG_MSM_SUBSYSTEM_RESTART
	obj-y += subsystem_notif.o
	obj-y += subsystem_restart.o
	obj-y += ramdump.o
endif
obj-$(CONFIG_MSM_SYSMON_COMM) += sysmon.o

#obj-$(CONFIG_CPU_IDLE) += cpuidle.o

obj-$(CONFIG_MSM_WATCHDOG) += msm_watchdog.o
obj-$(CONFIG_MSM_WATCHDOG) += msm_watchdog_asm.o
obj-$(CONFIG_MSM_WATCHDOG_V2) += msm_watchdog_v2.o
obj-$(CONFIG_MSM_MEMORY_DUMP) += msm_memory_dump.o

obj-$(CONFIG_ARCH_MSM8974) += clock-krait-8974.o board-8974.o clock-local2.o clock-pll.o clock-8974.o clock-rpm.o clock-voter.o clock-mdss-8974.o
obj-$(CONFIG_SEC_H_PROJECT) += board-8974-sec-h-gpiomux.o
obj-$(CONFIG_ARCH_MSM8974) += gdsc.o
obj-$(CONFIG_KRAIT_REGULATOR) += krait-regulator.o  krait-regulator-pmic.o

obj-$(CONFIG_MSM_PM) += msm-pm.o pm-data.o ext-buck-control.o

ifdef CONFIG_BCM4335
obj-$(CONFIG_ARCH_MSM8974) += board-8974-wifi.o board-8974-bt.o
endif

ifdef CONFIG_BCM4339
obj-$(CONFIG_ARCH_MSM8974) += board-8974-wifi.o board-8974-bt.o
endif

ifdef CONFIG_BCM4354
obj-$(CONFIG_ARCH_MSM8974) += board-8974-wifi.o board-8974-bt.o
endif

CFLAGS_msm_vibrator.o += -Idrivers/staging/android

obj-$(CONFIG_MSM_RPM) += rpm.o rpm_resources.o
obj-$(CONFIG_MSM_LPM_TEST) += test-lpm.o
obj-$(CONFIG_MSM_RPM_SMD) += rpm-smd.o lpm_levels.o
obj-$(CONFIG_MSM_MPM_OF) += mpm-of.o
obj-$(CONFIG_MSM_MPM) += mpm.o
obj-$(CONFIG_MSM_RPM_STATS_LOG) += rpm_stats.o rpm_master_stat.o
obj-$(CONFIG_MSM_RPM_RBCPR_STATS_LOG) += rpm_rbcpr_stats.o
obj-$(CONFIG_MSM_RPM_RBCPR_STATS_V2_LOG) += rpm_rbcpr_stats_v2.o
obj-$(CONFIG_MSM_RPM_LOG) += rpm_log.o
obj-$(CONFIG_MSM_TZ_LOG) += tz_log.o
obj-$(CONFIG_MSM_XO) += msm_xo.o
obj-$(CONFIG_MSM_BUS_SCALING) += msm_bus/
obj-$(CONFIG_MSM_BUSPM_DEV) += msm-buspm-dev.o
obj-$(CONFIG_USB_SWITCH_RT8973) += sec-switch.o
obj-$(CONFIG_REGULATOR_MAX77803) += sec-regulator-max77803.o
obj-$(CONFIG_USB_SWITCH_TSU6721) += sec-switch.o
obj-$(CONFIG_SM5502_MUIC) += sec-switch.o
obj-$(CONFIG_SM5504_MUIC) += sec-switch.o

ifdef CONFIG_EXTCON
obj-$(CONFIG_EXTCON) += board-extcon-connector.o
else
obj-$(CONFIG_MFD_MAX77803) += sec-switch.o
endif

obj-$(CONFIG_MSM_IOMMU) += iommu_domains.o

obj-$(CONFIG_MSM_EVENT_TIMER) += event_timer.o

obj-$(CONFIG_MSM_OCMEM) += ocmem.o ocmem_allocator.o ocmem_notifier.o
obj-$(CONFIG_MSM_OCMEM) += ocmem_sched.o ocmem_api.o ocmem_rdm.o ocmem_core.o
obj-$(CONFIG_SENSORS_ADSP) += sensors_adsp.o

obj-$(CONFIG_ARCH_MSM8974) += gpiomux-v2.o gpiomux.o

obj-$(CONFIG_MSM_SLEEP_STATS_DEVICE) += idle_stats_device.o
obj-$(CONFIG_MSM_DCVS) += msm_dcvs_scm.o msm_dcvs.o msm_mpdecision.o
obj-$(CONFIG_MSM_RUN_QUEUE_STATS) += msm_rq_stats.o
obj-$(CONFIG_MSM_SHOW_RESUME_IRQ) += msm_show_resume_irq.o
obj-$(CONFIG_BT_MSM_PINTEST)  += btpintest.o
obj-$(CONFIG_MSM_FAKE_BATTERY) += fish_battery.o
obj-$(CONFIG_MSM_RPC_VIBRATOR) += msm_vibrator.o
obj-$(CONFIG_MSM_NATIVE_RESTART) += restart.o
obj-$(CONFIG_MSM_MODEM_RESTART) += restart_7k.o

obj-$(CONFIG_MSM_PROC_COMM_REGULATOR) += proccomm-regulator.o

obj-$(CONFIG_SEC_DEBUG) += sec_debug.o sec_gaf.o sec_getlog.o
obj-$(CONFIG_SEC_DEBUG_DOUBLE_FREE) += sec_debug-dfd.o

obj-$(CONFIG_MSM_RTB) += msm_rtb.o
obj-$(CONFIG_MSM_CACHE_ERP) += cache_erp.o
obj-$(CONFIG_MSM_EBI_ERP) += ebi_erp.o
obj-$(CONFIG_MSM_CACHE_DUMP) += msm_cache_dump.o

obj-$(CONFIG_MSM_HSIC_SYSMON) += hsic_sysmon.o
obj-$(CONFIG_MSM_HSIC_SYSMON_TEST) += hsic_sysmon_test.o

obj-$(CONFIG_MSM_RPM_SMD) += rpm-smd.o
obj-$(CONFIG_MSM_CPR) += msm_cpr.o
obj-$(CONFIG_MSM_VP_REGULATOR) += msm_vp.o
obj-$(CONFIG_MSM_RPC_PMIC) += pmic.o
obj-$(CONFIG_MSM_RPC_USB) += rpc_hsusb.o rpc_fsusb.o
obj-$(CONFIG_MSM_RPC_PMAPP) += rpc_pmapp.o

obj-$(CONFIG_MSM_ENABLE_WDOG_DEBUG_CONTROL) += wdog_debug.o

obj-$(CONFIG_MSM_USE_USER_ACCESSIBLE_TIMERS) += timer_page.o

ifdef CONFIG_MSM_CPR
obj-$(CONFIG_DEBUG_FS) += msm_cpr-debug.o
endif
obj-$(CONFIG_MSM_FIQ) += msm7k_fiq.o
obj-$(CONFIG_MSM_FIQ) += msm7k_fiq_handler.o

obj-$(CONFIG_MEMORY_HOLE_CARVEOUT) +=  msm_mem_hole.o

obj-$(CONFIG_MSM_SMCMOD) += smcmod.o
obj-$(CONFIG_MSM_CPU_PWRCTL) +=  msm_cpu_pwrctl.o

obj-$(CONFIG_ARCH_MSM8974) += msm_mpmctr.o
obj-$(CONFIG_MSM_CPR_REGULATOR) += cpr-regulator.o
obj-$(CONFIG_CPU_FREQ_MSM) += cpufreq.o
obj-$(CONFIG_MSM_DEVFREQ_CPUBW) += devfreq_cpubw.o

obj-$(CONFIG_WALL_CLK) += wallclk.o
obj-$(CONFIG_WALL_CLK_SYSFS) += wallclk_sysfs.o

obj-$(CONFIG_BT_BCM4335) += board-bluetooth-bcm4335.o
obj-$(CONFIG_BT_BCM4339) += board-bluetooth-bcm4339.o
obj-$(CONFIG_BT_BCM4354) += board-bluetooth-bcm4354.o

obj-$(CONFIG_ARCH_RANDOM) += early_random.o
obj-$(CONFIG_PERFMAP) += perfmap.o

obj-$(CONFIG_SEC_BSP) += sec_bsp.o

ifdef CONFIG_ARCH_MSM8974
	obj-$(CONFIG_SEC_THERMISTOR) += sec_thermistor.o msm8974-thermistor.o
endif

obj-$(CONFIG_HAS_MACH_MEMUTILS) += memutils/

