include (${project_cmake_dir}/Utils.cmake)

set (headers
  AffineException.hh
  Angle.hh
  Box.hh
  Filter.hh
  Frustum.hh
  Helpers.hh
  IndexException.hh
  Kmeans.hh
  Line2.hh
  Line3.hh
  MassMatrix3.hh
  Matrix3.hh
  Matrix4.hh
  Plane.hh
  Pose3.hh
  Quaternion.hh
  Rand.hh
  RotationSpline.hh
  SignalStats.hh
  Spline.hh
  Triangle.hh
  Triangle3.hh
  Vector2.hh
  Vector3.hh
  Vector4.hh
)

set (ign_headers "" CACHE INTERNAL "Ignition math headers" FORCE)
foreach (hdr ${headers})
  APPEND_TO_CACHED_STRING(ign_headers
    "Ignition math headers" "#include <ignition/math/${hdr}>\n")
endforeach()

configure_file (${CMAKE_CURRENT_SOURCE_DIR}/math.hh.in
                ${CMAKE_CURRENT_BINARY_DIR}/math.hh)

ign_install_includes("${INCLUDE_INSTALL_DIR_POSTFIX}/ignition" ${CMAKE_CURRENT_BINARY_DIR}/math.hh)
ign_install_includes("${INCLUDE_INSTALL_DIR_POSTFIX}/ignition/${IGN_PROJECT_NAME}" ${headers})
