CMAKE_MINIMUM_REQUIRED(VERSION 2.6)

CMAKE_POLICY(SET CMP0048 OLD)

PROJECT(libtess)

SET(TESS_SRC
  dict.c  
  geom.c  
  # main.c  
  memalloc.c  
  mesh.c  
  normal.c  
  priorityq.c  
  # priorityq-heap.c  
  render.c  
  sweep.c  
  tess.c  
  tessellate.c  
  tessmono.c
)

INCLUDE_DIRECTORIES(include)

SET (CMAKE_POSITION_INDEPENDENT_CODE TRUE)

ADD_LIBRARY(tess STATIC ${TESS_SRC})
TARGET_LINK_LIBRARIES(tess m)

# ADD_EXECUTABLE(tess_example main.c)
# TARGET_LINK_LIBRARIES(tess_example tess)


target_link_libraries(tess PUBLIC "-framework Foundation -framework AVFoundation -framework SystemConfiguration -framework AssetsLibrary -framework OpenGLES \
    -framework CoreText -framework QuartzCore -framework CoreGraphics -framework ImageIO -framework Security -framework UIKit -framework WebKit \
    -framework CoreBluetooth -framework MobileCoreServices -framework QuickLook -framework AudioToolbox -framework CoreLocation \
    -framework Accelerate -framework CoreMedia -framework CoreVideo -framework MediaToolbox -framework MediaPlayer -framework GameController
    -framework CoreMotion -framework StoreKit -weak_framework Metal -lz")

IF(${CMAKE_SYSTEM_NAME} STREQUAL "iOS")
    INCLUDE("${CMAKE_SOURCE_DIR}/cmake/AddQtIosApp.cmake")
    add_qt_ios_app(tess
        NAME "tess"
        BUNDLE_IDENTIFIER "2T2FTL85G3.ch.opengis.qfield"
        PRODUCT_BUNDLE_IDENTIFIER "ch.opengis.qfield"
        VERSION "1.2.3"
        SHORT_VERSION "1.2.3"
        LONG_VERSION "1.2.3.456"
        CUSTOM_PLIST "MacOSXBundleInfo.plist.in"
        CODE_SIGN_IDENTITY "iPhone Developer"
        TEAM_ID "2T2FTL85G3"
        ORIENTATION_PORTRAIT
        ORIENTATION_PORTRAIT_UPSIDEDOWN
        ORIENTATION_LANDSCAPELEFT
        ORIENTATION_LANDSCAPERIGHT
        SUPPORT_IPHONE
        SUPPORT_IPAD
        REQUIRES_FULL_SCREEN
        HIDDEN_STATUS_BAR
        VERBOSE
    )
ENDIF()