cmake_minimum_required(VERSION 3.12)

project(Cosserat_SRC)

set(HEADER_FILES
    config.h.in
    fwd.h
    types.h
    initCosserat.cpp
    engine/GeometricStiffnessEngine.h
    engine/GeometricStiffnessEngine.inl
    engine/CosseratBeamGeometryEngine.h
    forcefield/BeamHookeLawForceField.h
    forcefield/BeamHookeLawForceField.inl
    mapping/CosseratNonLinearMapping2D.h
    mapping/CosseratNonLinearMapping2D.inl
    mapping/DifferenceMultiMapping.h
    mapping/DifferenceMultiMapping.inl
    constraint/UnilateralPlaneConstraint.h
    constraint/UnilateralPlaneConstraint.inl
    engine/CosseratTopologyBuilder.h
    engine/CosseratIntrinsicState.h
    engine/PainlessBeamForceField.h
    mapping/StaggeredCosseratMapping.h
)

set(SOURCE_FILES
    initCosserat.cpp
    engine/GeometricStiffnessEngine.cpp
    engine/CosseratBeamGeometryEngine.cpp
=======
    config.h

    mapping/BaseCosserat.h
    mapping/BaseCosserat.inl
    mapping/BeamContactMapping.h
    mapping/BeamContactMapping2.h
    mapping/DiscreteCosseratMapping.h
    mapping/DiscreteCosseratMapping.inl
    mapping/DiscretDynamicCosseratMapping.h
    mapping/DiscreteDynamicCosseratMapping.inl
    mapping/DifferenceMultiMapping.h
    mapping/DifferenceMultiMapping.inl
    mapping/RigidDistanceMapping.h
    mapping/RigidDistanceMapping.inl
    mapping/LegendrePolynomialsMapping.h
    mapping/LegendrePolynomialsMapping.inl
    
    engine/ProjectionEngine.h
    engine/ProjectionEngine.inl
    engine/ContactTriad.h



    forcefield/BeamHookeLawForceField.h
    forcefield/BeamHookeLawForceField.inl
    forcefield/BeamHookeLawForceFieldRigid.h
    forcefield/BeamHookeLawForceFieldRigid.inl
    forcefield/CosseratInternalActuation.h
    forcefield/CosseratInternalActuation.inl
    forcefield/MyUniformVelocityDampingForceField.h
    forcefield/MyUniformVelocityDampingForceField.inl

    constraint/CosseratSlidingConstraint.h
    constraint/CosseratSlidingConstraint.inl
    constraint/QPSlidingConstraint.h
    constraint/QPSlidingConstraint.inl
    constraint/CosseratNeedleSlidingConstraint.h
    constraint/CosseratNeedleSlidingConstraint.inl
    constraint/ContactPointsUnilateralConstraint.h

    intersection/SphereSweptIntersectionMethod.h
    intersection/SphereSweptIntersectionMethod2.h

    )

set(SOURCE_FILES
    initCosserat.cpp

    mapping/BaseCosserat.cpp
    mapping/BeamContactMapping.cpp
    mapping/BeamContactMapping2.cpp
    mapping/DiscreteCosseratMapping.cpp
    mapping/DiscreteDynamicCosseratMapping.cpp
    mapping/DifferenceMultiMapping.cpp
    mapping/RigidDistanceMapping.cpp
    mapping/LegendrePolynomialsMapping.cpp

    engine/ProjectionEngine.cpp

>>>>>>> zawada/CTR_AWADA
    forcefield/BeamHookeLawForceField.cpp
    mapping/CosseratNonLinearMapping2D.cpp
    mapping/DifferenceMultiMapping.cpp
    constraint/UnilateralPlaneConstraint.cpp
    engine/CosseratTopologyBuilder.cpp
    engine/CosseratIntrinsicState.cpp
    engine/PainlessBeamForceField.cpp
    mapping/StaggeredCosseratMapping.cpp
)

find_package(SofaFramework REQUIRED)
find_package(SofaBase REQUIRED)
find_package(SofaOpenglVisual REQUIRED)
find_package(Geometric_stiffness REQUIRED)
find_package(Eigen3 REQUIRED)
    
constraint/CosseratSlidingConstraint.cpp
constraint/QPSlidingConstraint.cpp
constraint/CosseratNeedleSlidingConstraint.cpp
constraint/ContactPointsUnilateralConstraint.cpp
intersection/SphereSweptIntersectionMethod.cpp 

add_library(${PROJECT_NAME} SHARED ${HEADER_FILES} ${SOURCE_FILES})
target_link_libraries(${PROJECT_NAME} PUBLIC
    SofaBase
    SofaOpenglVisual
    Geometric_stiffness
)
target_include_directories(${PROJECT_NAME} PUBLIC "$<BUILD_INTERFACE:${CMAKE_CURRENT_SOURCE_DIR}/..>")
target_include_directories(${PROJECT_NAME} PUBLIC ${EIGEN3_INCLUDE_DIR})

set_target_properties(${PROJECT_NAME} PROPERTIES COMPILE_FLAGS "-DSOFA_BUILD_COSSERAT")
