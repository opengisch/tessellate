cmake_minimum_required(VERSION 2.6)

project(libtess)

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

add_library(tess SHARED ${TESS_SRC})
target_link_libraries(tess m)

add_executable(tess_example main.c)
target_link_libraries(tess_example tess)
