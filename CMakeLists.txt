cmake_minimum_required(VERSION 3.15)
project(aggtest VERSION 0.0.0 LANGUAGES C CXX)

set(CMAKE_CXX_STANDARD 17)

set(MY_SOURCES
    agg-src/src/agg_arc.cpp
    agg-src/src/agg_arrowhead.cpp
    agg-src/src/agg_bezier_arc.cpp
    agg-src/src/agg_bspline.cpp
    agg-src/src/agg_color_rgba.cpp
    agg-src/src/agg_curves.cpp
    agg-src/src/agg_embedded_raster_fonts.cpp
    agg-src/src/agg_gsv_text.cpp
    agg-src/src/agg_image_filters.cpp
    agg-src/src/agg_line_aa_basics.cpp
    agg-src/src/agg_line_profile_aa.cpp
    agg-src/src/agg_rounded_rect.cpp
    agg-src/src/agg_sqrt_tables.cpp
    agg-src/src/agg_trans_affine.cpp
    agg-src/src/agg_trans_double_path.cpp
    agg-src/src/agg_trans_single_path.cpp
    agg-src/src/agg_trans_warp_magnifier.cpp
    agg-src/src/agg_vcgen_bspline.cpp
    agg-src/src/agg_vcgen_contour.cpp
    agg-src/src/agg_vcgen_dash.cpp
    agg-src/src/agg_vcgen_markers_term.cpp
    agg-src/src/agg_vcgen_smooth_poly1.cpp
    agg-src/src/agg_vcgen_stroke.cpp
    agg-src/src/agg_vpgen_clip_polygon.cpp
    agg-src/src/agg_vpgen_clip_polyline.cpp
    agg-src/src/agg_vpgen_segmentator.cpp

    agg-src/src/ctrl/agg_bezier_ctrl.cpp
    agg-src/src/ctrl/agg_cbox_ctrl.cpp
    agg-src/src/ctrl/agg_gamma_ctrl.cpp
    agg-src/src/ctrl/agg_gamma_spline.cpp
    agg-src/src/ctrl/agg_polygon_ctrl.cpp
    agg-src/src/ctrl/agg_rbox_ctrl.cpp
    agg-src/src/ctrl/agg_scale_ctrl.cpp
    agg-src/src/ctrl/agg_slider_ctrl.cpp
    agg-src/src/ctrl/agg_spline_ctrl.cpp
    )

set(MY_INCLUDE
    agg-src/include
    agg-src/agg2d

)

set(MY_DEFINITIONS

)

if (WIN32)
    list(APPEND MY_SOURCES
        agg-src/font_win32_tt/agg_font_win32_tt.cpp
        agg-src/src/platform/win32/agg_platform_support.cpp
        agg-src/src/platform/win32/agg_win32_bmp.cpp
        )
    list(APPEND MY_INCLUDE
        agg-src/font_win32_tt
        )
    list(APPEND MY_DEFINITIONS
        _CRT_SECURE_NO_WARNINGS
        )

    add_executable(agg_demo WIN32 ${MY_SOURCES}

        # agg-src/myapp/agg2d_demo.cpp
        agg-src/myapp/my_demo.cpp
    )

endif()



target_include_directories(agg_demo PRIVATE ${MY_INCLUDE})
target_compile_definitions(agg_demo PRIVATE ${MY_DEFINITIONS})
target_compile_options(agg_demo PRIVATE
    -Wno-switch
    -Wno-unused-function
    -Wno-unused-but-set-variable
    -Wno-reorder-ctor
    -Wno-unused-const-variable
    )