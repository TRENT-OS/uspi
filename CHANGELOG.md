# Changelog

All notable changes by HENSOLDT Cyber GmbH to this 3rd party module included in
the TRENTOS-M SDK will be documented in this file.

For more details it is recommended to compare the 3rd party module at hand with
the previous versions of the TRENTOS-M SDK or the baseline version.

## [1.1]

### Fixed

- Tune delay values to avoid seL4 error messages in functions
`DWHCIDeviceTransferStage`, `DWHCIDeviceFlushRxFIFO`, `DWHCIDeviceFlushTxFIFO`.

## [1.0]

### Changed

- Synchronize send and receive in function `DWHCIDeviceTransferStage` and
improve performance by adding a delay to the busy-waiting loop.

## [0.9]

### Changed

- Replace `malloc`/`free` with `dma_alloc`/`dma_free` wherever the allocated
memory is used for DMA. These functions are defined inside `uspios.h` and are
implemented alongside other environment functions.
- Rename error codes from `LOG_ERROR` to `USPI_LOG_ERROR` to avoid clashes with
environment error codes and added more log output to make the internal states
more understandable during runtime.
- Make the interrupt handler `DWHCIDeviceInterruptHandler` public so it can be
called from the environment interrupt handler that actually gets triggered on
interrupt.
- Add a static reference to `self` which can be accessed from the interrupt
handler `DWHCIDeviceInterruptHandler` since the environment interrupt handler
does not support registering this reference internally.

### Added

- Start development based on USPi library 2.00 from
<https://github.com/rsta2/uspi>.
