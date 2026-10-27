# RV1103B Release Note

## rv1103b_spl_v5_v1.00.bin

| Date       | File                     | Build commit | Severity  |
| ---------- | :----------------------- | ------------ | -------- |
| 2026-10-27 | rv1103b_spl_v5_v1.00.bin | f27a0645d26d | important |

### New

1. Initial version based on U-Boot v5 branch.

------

## rv1103b_ddr_864MHz{_tb}_v1.09.bin

| Date       | File                              | Build commit | Severity  |
| ---------- | :-------------------------------- | ------------ | --------- |
| 2026-10-26 | rv1103b_ddr_864MHz{_tb}_v1.09.bin | a27d08667d   | important |

### New

1. Add support for RV1106BS.

### Fixed

| Index | Severity  | Update                         | Issue description      | Issue source |
| ----- | --------- | ------------------------------ | ---------------------- | ------------ |
| 1     | important | Adjust DQS OE timing           | Improve DDR stability  | -            |
| 2     | important | Tune DDR2 signal configuration | Improve DDR2 stability | -            |

------

## rv1103b_spl_v1.02.bin

| Date       | File                  | Build commit | Severity  |
| ---------- | :-------------------- | ------------ | --------- |
| 2026-10-23 | rv1103b_spl_v1.02.bin | ab071d7ddfc  | important |

### New

1. Add RV1106BS secure efuse support and fix RV1103B legacy secure OTP layout compatibility, so the secure boot enable flag and RSA key hash are read correctly on both RV1103B and RV1106BS.
2. Fix SPL A/B rollback index read: after the function naming alignment, the rollback index override in SPL takes effect again.
3. Update the SPL thunderboot entry blob shared by RV1103B/RV1106.
4. Print board "Model: xxx" in the SPL serial log.
5. Fix SPI NAND/NOR boot storage issues: wrong spi_slave pointer in SFC probe corrupting DM memory, SFC delay lines not reset before tuning, MTD BLK large reads not chunked by max_read_size, SPI_DMA_PREPARE wrongly cleared in partial read, and wrong ending_lba of GPT in SPI NAND factory mode.
6. Fix eMMC boot issues: extend the CMD1 retry timeout to 1 second, stop sending CMD16 to set block length on eMMC, and fix dw_mmc incorrectly skipping sample clock configuration.
7. Add support for more SPI NAND / SPI NOR devices, fix device parameters, and remove QUADIO read-cache variants and duplicate entries.
8. Skip the legacy pinctrl-rockchip driver for RV1103B to reduce SPL size.

------

## rv1103b_tee_ta_v1.07.bin

| Date       | File                     | Build commit | Severity  |
| ---------- | :----------------------- | ------------ | --------- |
| 2026-10-16 | rv1103b_tee_ta_v1.07.bin | a71726aef    | important |

### New

1. Compatible with RV1103BS/RV1106BS platforms.

------

## rv1103b_hpmcu_wrap_v2.04rc7.bin

| Date       | File                            | Build commit | Severity  |
| ---------- | ------------------------------- | ------------ | --------- |
| 2026-09-30 | rv1103b_hpmcu_wrap_v2.04rc7.bin | 8631322      | important |

### New

1. Upgrade RV1103B HPMCU wrap firmware to v2.04rc7.
2. Adapt RKTRUST/RV1103BTOS_MCU_WRAP.ini MCU0 path.

------

## rv1103b_tee_ta_v1.06.bin

| Date       | File                     | Build commit | Severity  |
| ---------- | :----------------------- | ------------ | --------- |
| 2026-09-24 | rv1103b_tee_ta_v1.06.bin | e48c4cffb    | important |

### New

1. Support the use of RSA public keys with lengths of 3072 and 4096 to replace the default public key in the TEE OS firmware.

### Fixed

| Index | Severity  | Update                                                       | Issue description                                            | Issue source |
| ----- | --------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------ |
| 1     | important | If the serial port is halted, no information will be printed | The non-secure world may halt the serial port, resulting in timeouts in serial port printing in the secure world, which in turn leads to timeouts in responding to external interrupts | 610227       |
| 2     | important | Fix the panic caused by RSA verification failure             | A failure in RSA verification may inadvertently trigger an fault injection attack, resulting in a TEE OS panic | 639776       |
| 3     | important | Fix crypto_service reserved field size mismatch with 32-bit TA | The 32-bit TA passes a 100-byte rk_cipher_config/rk_aead_config buffer, while the 64-bit TEE OS expects 104 bytes (8-byte void* reserved field), so the size check rejects the TA request | 646458       |
| 4     | important | Integrate CVE patchs                                         | CVE-2026-53764<br />CVE-2026-85059<br />CVE-2026-42546<br />CVE-2025-10263<br />CVE-2026-41434<br />CVE-2026-53763<br />CVE-2026-45614<br />CVE-2026-33662<br />CVE-2026-33317<br />CVE-2025-46733 | -            |

------

## rv1103b_ddr_864MHz{_tb}_v1.08.bin

| Date       | File                              | Build commit | Severity  |
| ---------- | :-------------------------------- | ------------ | --------- |
| 2026-08-27 | rv1103b_ddr_864MHz{_tb}_v1.08.bin | fd3fd307c5   | important |

### Fixed

| Index | Severity  | Update                                                | Issue description           | Issue source |
| ----- | --------- | ----------------------------------------------------- | --------------------------- | ------------ |
| 1     | important | Disable auto sr and pd by default                     | Improve stability           | -            |
| 2     | important | Adjust DDR3 default frequency to 864MHz and optimize SI configuration | Improve stability | -            |
| 3     | important | Optimize rd/wr training parameters and flow           | Improve stability           | -            |
| 4     | important | Optimize gate training flow for 8-bit DDR             | Improve 8-bit DDR stability | -            |

------

## rv1103b_ddr_924MHz{_tb}_v1.07.bin

| Date       | File                              | Build commit | Severity  |
| ---------- | :-------------------------------- | ------------ | --------- |
| 2026-06-18 | rv1103b_ddr_924MHz{_tb}_v1.07.bin | 2bf646c6e6   | important |

### New

1. Add non-KGD package support.
2. Add support for 8-bit bus width detection.

------

## rv1103b_tee_ta_v1.05.bin

| Date       | File                     | Build commit | Severity  |
| ---------- | :----------------------- | ------------ | --------- |
| 2026-04-29 | rv1103b_tee_ta_v1.05.bin | 5f256dc1a    | important |

### New

1. OAEP decode compatible with MGF1 = SHA1.
2. Optimize sleep and wake-up.

### Fixed

| Index | Severity  | Update                                   | Issue description                                            | Issue source |
| ----- | --------- | ---------------------------------------- | ------------------------------------------------------------ | ------------ |
| 1     | important | Fix the low-probability data abort issue | The reboot of the device during secure storage may trigger it with a low probability | -            |

------

## rv1103b_spl_v1.01.bin

| Date       | File                  | Build commit | Severity  |
| ---------- | :----------------------- | ----------- | -------- |
| 2026-03-02 | rv1103b_spl_v1.01.bin | a27a89c5fa1   | important     |

### Fixed

| Index | Severity  | Update                                  | Issue description                   | Issue source |
| ----- | --------- | --------------------------------------- | ----------------------------------- | ------------ |
| 1     | important  | Avoid premature decompression termination by decom. | SPL hw decompression of uboot failed. | -            |

------

## rv1103b_usbplug_auto_merge_v1.11.bin

| Date       | File                               | Build commit                                   | Severity |
| ---------- | :--------------------------------- | ---------------------------------------------- | -------- |
| 2026-02-10 | rv1103b_usbplug_auto_merge_v1.11.bin | 3bb9568b5 | moderate |

### New

1. Enable SFDP.

------

## rv1103b_ddr_924MHz{_tb}_v1.06.bin

| Date       | File                              | Build commit | Severity  |
| ---------- | :-------------------------------- | ------------ | --------- |
| 2025-10-10 | rv1103b_ddr_924MHz{_tb}_v1.06.bin | b971cce143   | important |

### New

1. Weak pull up UART0M0 RX to prevent it from being switched to JTAG.
2. Add rzq calibration function.

### Fixed

| Index | Severity  | Update                               | Issue description                                            | Issue source |
| ----- | --------- | ------------------------------------ | ------------------------------------------------------------ | ------------ |
| 1     | important | Fixing DDR initialization hang issue | Board with high PLL power supply ripple exhibits intermittent boot hang | -            |
| 2     | important | Fixing gate training abnormal issue  | Intermittent training result anomaly with boot failure       | -            |

------

## rv1103b_usbplug_spinand_cont_v1.10.bin

| Date       | File                     | Build commit | Severity  |
| ---------- | :----------------------- | ------------ | --------- |
| 2025-07-28 | rv1103b_usbplug_spinand_cont_v1.10.bin | d86aef4ef0d3    | moderate |

### New

1. Support mxic and gigadevice spinand continues read mode.

------

## rv1103b_tee_ta_v1.04.bin

| Date       | File                     | Build commit | Severity  |
| ---------- | :----------------------- | ------------ | --------- |
| 2025-07-04 | rv1103b_tee_ta_v1.04.bin | 76f8f9d23    | important |

### New

1. Support User TA to use OEM OTP KEY for encryption and decryption calculations.

### Fixed

| Index | Severity  | Update                          | Issue description                  | Issue source |
| ----- | --------- | ------------------------------- | ---------------------------------- | ------------ |
| 1     | important | Merge official security patches | Address potential security risks   | -            |
| 2     | important | Reduce shared memory size       | Compatible with 64M memory devices | -            |

------

## rv1103b_tee_ta_v1.03.bin

| Date       | File                     | Build commit | Severity  |
| ---------- | :----------------------- | ------------ | --------- |
| 2024-12-17 | rv1103b_tee_ta_v1.03.bin | 6b118d039    | important |

### New

1. Supports hardware crypto and true random number generator TRNG.

------

## rv1103b_tee_ta_v1.02.bin

| Date       | File                     | Build commit | Severity  |
| ---------- | :----------------------- | ------------ | --------- |
| 2024-11-01 | rv1103b_tee_ta_v1.02.bin | 9f2aca7d1    | important |

### Fixed

| Index | Severity  | Update                                                       | Issue description                                            | Issue source |
| ----- | --------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ------------ |
| 1     | important | check whether the rpmb key has been burned before changing security level | upgrading from weak security level to strong security level may result in rpmb key verification failure | -            |
| 2     | important | fixed RSA OAEP MGF1 algorithm                                | TA will report an error when using RSA algorithm OAEP MGF1 padding method | -            |

------

## rv1103b_hpmcu_wrap_v2.02.bin

| Date       | File                         | Build commit     | Severity  |
| ---------- | :--------------------------- | ---------------- | --------- |
| 2024-10-22 | rv1103b_hpmcu_wrap_v2.02.bin | rockit_ko:26f0ca4 | important |

### New

1. Support double channel wrap.

------

## rv1103b_ddr_924MHz{_tb}_v1.05.bin

| Date       | File                              | Build commit | Severity  |
| ---------- | :-------------------------------- | ------------ | --------- |
| 2024-10-14 | rv1103b_ddr_924MHz{_tb}_v1.05.bin | a0d2414c29   | important |

### Fixed

| Index | Severity  | Update                                          | Issue description | Issue source |
| ----- | --------- | ----------------------------------------------- | ----------------- | ------------ |
| 1     | important | Fix DDR3 924MHz probabilistic resume hang issue | -                 | -            |

------

## rv1103b_tee_ta_v1.01.bin

| Date       | File                     | Build commit | Severity  |
| ---------- | :----------------------- | ------------ | --------- |
| 2024-10-14 | rv1103b_tee_ta_v1.01.bin | 066b2fbeb    | important |

### New

1. Modify the TEE loading address to 62M.

------


## rv1103b_flash_acc_w25n01xx_v1.00.bin

| Date       | File                              | Build commit | Severity  |
| ---------- | :--------------------------------------- | ----------- | -------- |
| 2024-10-08 | rv1103b_flash_acc_w25n01xx_v1.00.bin        | c2c14bb7e419  | important     |

### New

1. Add w25n01jw rom accelerator.

------

## rv1103b_usbplug_auto_merge_v1.10.bin

| Date       | File                               | Build commit                                   | Severity |
| ---------- | :--------------------------------- | ---------------------------------------------- | -------- |
| 2024-09-29 | rv1103b_usbplug_auto_merge_v1.10.bin | f9ecba2b | moderate |

### New

1. Change cs1 to gpio2a6.

------

## rv1103b_usbplug_auto_merge_v1.00.bin

| Date       | File                               | Build commit                                   | Severity |
| ---------- | :--------------------------------- | ---------------------------------------------- | -------- |
| 2024-09-25 | rv1103b_usbplug_auto_merge_v1.00.bin | a87eca5 | moderate |

### New

1. Initial version.

------

## rv1103b_ddr_924MHz{_tb}_v1.04.bin

| Date       | File                              | Build commit | Severity  |
| ---------- | :-------------------------------- | ------------ | --------- |
| 2024-08-30 | rv1103b_ddr_924MHz{_tb}_v1.04.bin | ccb664bdcf   | important |

### New

1. Improve DDR stability.

------

## rv1103b_ddr_924MHz{_tb}_v1.03.bin

| Date       | File                              | Build commit | Severity  |
| ---------- | :-------------------------------- | ------------ | --------- |
| 2024-08-26 | rv1103b_ddr_924MHz{_tb}_v1.03.bin | b991ae72ff   | important |

### Fixed

| Index | Severity  | Update                                   | Issue description | Issue source |
| ----- | --------- | ---------------------------------------- | ----------------- | ------------ |
| 1     | important | Fix gate training timeout of DDR2 528MHz | -                 | -            |
| 2     | important | Fix isp mipi drop when 4M 60fps          | -                 | -            |
| 3     | important | Fix DDR setting for power-saving         | -                 | -            |

------

## rv1103b_tee_ta_v1.00.bin

| Date       | File                     | Build commit | Severity  |
| ---------- | :----------------------- | ------------ | --------- |
| 2024-08-20 | rv1103b_tee_ta_v1.00.bin | ed4478bc9    | important |

### New

1. Add OPTEE support.

------

## rv1103b_{ddr,spl,usbplug,hpmcu}_v1.00.bin

| Date       | File                               | Build commit                                   | Severity |
| ---------- | :--------------------------------- | ---------------------------------------------- | -------- |
| 2024-07-29 | rv1103b_{ddr,spl,usbplug,hpmcu}_v1.00.bin | ddr:1b742cd9d6#spl:3687236ab1c:usbplug:c53c564#rtt:3143c22c#hal:939ec3d5#battery_ipc:06ccc158 | moderate |

### New

1. Initial version.

------

