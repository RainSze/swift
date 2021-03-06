cmake_minimum_required(VERSION 3.4.3)
include("../../../../cmake/modules/StandaloneOverlay.cmake")

add_swift_library(swiftWatchKit ${SWIFT_SDK_OVERLAY_LIBRARY_BUILD_TYPES} IS_SDK_OVERLAY
  WKInterfaceController.swift

  SWIFT_COMPILE_FLAGS "${SWIFT_RUNTIME_SWIFT_COMPILE_FLAGS}"
  LINK_FLAGS "${SWIFT_RUNTIME_SWIFT_LINK_FLAGS}"
  TARGET_SDKS IOS IOS_SIMULATOR WATCHOS WATCHOS_SIMULATOR
  SWIFT_MODULE_DEPENDS_IOS Darwin CoreGraphics CoreImage CoreLocation Dispatch Foundation MapKit ObjectiveC os QuartzCore UIKit XPC # auto-updated
  SWIFT_MODULE_DEPENDS_WATCHOS Darwin CoreGraphics CoreImage CoreLocation Dispatch Foundation HomeKit MapKit ObjectiveC QuartzCore SceneKit simd UIKit XPC # auto-updated
  FRAMEWORK_DEPENDS_WEAK WatchKit
  SWIFT_COMPILE_FLAGS_WATCHOS -Xfrontend -disable-autolink-framework -Xfrontend CoreText

  DEPLOYMENT_VERSION_IOS ${SWIFTLIB_DEPLOYMENT_VERSION_WATCHKIT_IOS}
  DEPLOYMENT_VERSION_WATCHOS ${SWIFTLIB_DEPLOYMENT_VERSION_WATCHKIT_WATCHOS}
)
