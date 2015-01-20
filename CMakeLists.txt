CMAKE_MINIMUM_REQUIRED(VERSION 2.6)

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
