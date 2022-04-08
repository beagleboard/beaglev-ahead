# BeagleV-Ahead

* T-Head TH1520 AI system-on-chip processor
   * Quad-core XuanTie C910 open-source RTL RISC-V (RV64GCV ISA) CPU @ 2GHz
     * 3 issue, 8 instruction, 9-12 stage pipeline
     * In-order fetch, out-of-order launch, out-of-order completion and in-order retirement
     * 64KB I-cache, 64KB D-cache per core
   * AI NPU with 4TOPS INT8 @ 1GHz
     * Support for TensorFlow, ONNX, Caffe
     * Feature extraction accelerator
   * Image signal processor
   * H.264/H.265/JPEG video encoder and decoder
   * 2D accelerator
   * 3D Vulkan/OpenCL/OpenGLES accelerator (IMG?)
   * C906-based (RV64IMA\[FD]C\[V] ISA) audio processor subsystem
* 4GB LPDDR4
* 16GB eMMC
* BeagleBone AI-64 form-factor open-source development board
   * ~2xSuperSpeed-USB type-A host (stacked)~
   * SuperSpeed USB type-C dual-role with power input (no power output)
   * Consider adding USB-to-serial/JTAG for the type-C device and move USB to host-only
   * Gigabit Ethernet with speed/connection indicators
   * HDMI type-A connector
   * TBD SDIO WiFi
   * uSD card cage
   * 2xCSI ribbon cable connectors
   * 1xDSI ribbon cable connector
   * 2x46-pin expansion headers with 4-pin HS-USB extension
   * 2x8-pin "mikroBus shuttle" ribbon-cable connector for audio and sensors
   * 3-pin TTL-level debug UART connector
   * Fan power connector (fan is optional)
   * 6x LEDs (1 power, 5 programmable)
   * 3x push-buttons (power, reset, boot/user)
   * 5V barrel jack
* BeagleBoard.org Debian Linux image
   * Tracking mainline u-boot/kernel with T-Head patches as needed
   * Package feeds for custom binaries for TensorFlow Lite, etc.
   * Familiar and flexible graphical user interface environment
   * Self-hosted Visual Studio Code IDE via web-browser
   * USB-based virtual network for "single-cable development"
