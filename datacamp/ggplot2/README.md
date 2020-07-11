---
description: explore and explain
---

# GGPLOT2

"[https://ggplot2.tidyverse.org/reference/index.html](https://ggplot2.tidyverse.org/reference/index.html)"

## Layers

### Geom

A layer combines data, aesthetic mapping, a geom \(geometric object\), a stat \(statistical transformation\), and a position adjustment. Typically, you will create layers using a `geom_` function, overriding the default position and stat if needed.

| shape | functions | notes |
| :--- | :--- | :--- |
| [![](https://ggplot2.tidyverse.org/reference/icons/geom_abline.png)](https://ggplot2.tidyverse.org/reference/geom_abline.html) | [`geom_abline()`](https://ggplot2.tidyverse.org/reference/geom_abline.html) [`geom_hline()`](https://ggplot2.tidyverse.org/reference/geom_abline.html) [`geom_vline()`](https://ggplot2.tidyverse.org/reference/geom_abline.html) | Reference lines: horizontal, vertical, and diagonal |
| [![](https://ggplot2.tidyverse.org/reference/icons/geom_bar.png)](https://ggplot2.tidyverse.org/reference/geom_bar.html) | [`geom_bar()`](https://ggplot2.tidyverse.org/reference/geom_bar.html) [`geom_col()`](https://ggplot2.tidyverse.org/reference/geom_bar.html) [`stat_count()`](https://ggplot2.tidyverse.org/reference/geom_bar.html) | Bar charts |
| [![](https://ggplot2.tidyverse.org/reference/icons/geom_bin2d.png)](https://ggplot2.tidyverse.org/reference/geom_bin2d.html) | [`geom_bin2d()`](https://ggplot2.tidyverse.org/reference/geom_bin2d.html) [`stat_bin_2d()`](https://ggplot2.tidyverse.org/reference/geom_bin2d.html) | Heatmap of 2d bin counts |
| [![](https://ggplot2.tidyverse.org/reference/icons/geom_blank.png)](https://ggplot2.tidyverse.org/reference/geom_blank.html) | [`geom_blank()`](https://ggplot2.tidyverse.org/reference/geom_blank.html) | Draw nothing |
| [![](https://ggplot2.tidyverse.org/reference/icons/geom_boxplot.png)](https://ggplot2.tidyverse.org/reference/geom_boxplot.html) | [`geom_boxplot()`](https://ggplot2.tidyverse.org/reference/geom_boxplot.html) [`stat_boxplot()`](https://ggplot2.tidyverse.org/reference/geom_boxplot.html) | A box and whiskers plot \(in the style of Tukey\) |
| [![](https://ggplot2.tidyverse.org/reference/icons/geom_contour.png)](https://ggplot2.tidyverse.org/reference/geom_contour.html) | [`geom_contour()`](https://ggplot2.tidyverse.org/reference/geom_contour.html) [`geom_contour_filled()`](https://ggplot2.tidyverse.org/reference/geom_contour.html) [`stat_contour()`](https://ggplot2.tidyverse.org/reference/geom_contour.html) [`stat_contour_filled()`](https://ggplot2.tidyverse.org/reference/geom_contour.html) | 2D contours of a 3D surface |
| [![](https://ggplot2.tidyverse.org/reference/icons/geom_count.png)](https://ggplot2.tidyverse.org/reference/geom_count.html) | [`geom_count()`](https://ggplot2.tidyverse.org/reference/geom_count.html) [`stat_sum()`](https://ggplot2.tidyverse.org/reference/geom_count.html) | Count overlapping points |
| [![](https://ggplot2.tidyverse.org/reference/icons/geom_density.png)](https://ggplot2.tidyverse.org/reference/geom_density.html) | [`geom_density()`](https://ggplot2.tidyverse.org/reference/geom_density.html) [`stat_density()`](https://ggplot2.tidyverse.org/reference/geom_density.html) | Smoothed density estimates |
|  | [`geom_density_2d()`](https://ggplot2.tidyverse.org/reference/geom_density_2d.html) [`geom_density_2d_filled()`](https://ggplot2.tidyverse.org/reference/geom_density_2d.html) [`stat_density_2d()`](https://ggplot2.tidyverse.org/reference/geom_density_2d.html) [`stat_density_2d_filled()`](https://ggplot2.tidyverse.org/reference/geom_density_2d.html) | Contours of a 2D density estimate |
| [![](https://ggplot2.tidyverse.org/reference/icons/geom_dotplot.png)](https://ggplot2.tidyverse.org/reference/geom_dotplot.html) | [`geom_dotplot()`](https://ggplot2.tidyverse.org/reference/geom_dotplot.html) | Dot plot |
|  | [`geom_errorbarh()`](https://ggplot2.tidyverse.org/reference/geom_errorbarh.html) | Horizontal error bars |
|  | [`geom_function()`](https://ggplot2.tidyverse.org/reference/geom_function.html) [`stat_function()`](https://ggplot2.tidyverse.org/reference/geom_function.html) | Draw a function as a continuous curve |
| [![](https://ggplot2.tidyverse.org/reference/icons/geom_hex.png)](https://ggplot2.tidyverse.org/reference/geom_hex.html) | [`geom_hex()`](https://ggplot2.tidyverse.org/reference/geom_hex.html) [`stat_bin_hex()`](https://ggplot2.tidyverse.org/reference/geom_hex.html) | Hexagonal heatmap of 2d bin counts |
| [![](https://ggplot2.tidyverse.org/reference/icons/geom_freqpoly.png)](https://ggplot2.tidyverse.org/reference/geom_histogram.html) | [`geom_freqpoly()`](https://ggplot2.tidyverse.org/reference/geom_histogram.html) [`geom_histogram()`](https://ggplot2.tidyverse.org/reference/geom_histogram.html) [`stat_bin()`](https://ggplot2.tidyverse.org/reference/geom_histogram.html) | Histograms and frequency polygons |
| [![](https://ggplot2.tidyverse.org/reference/icons/geom_jitter.png)](https://ggplot2.tidyverse.org/reference/geom_jitter.html) | [`geom_jitter()`](https://ggplot2.tidyverse.org/reference/geom_jitter.html) | Jittered points |
| [![](https://ggplot2.tidyverse.org/reference/icons/geom_crossbar.png)](https://ggplot2.tidyverse.org/reference/geom_linerange.html) | [`geom_crossbar()`](https://ggplot2.tidyverse.org/reference/geom_linerange.html) [`geom_errorbar()`](https://ggplot2.tidyverse.org/reference/geom_linerange.html) [`geom_linerange()`](https://ggplot2.tidyverse.org/reference/geom_linerange.html) [`geom_pointrange()`](https://ggplot2.tidyverse.org/reference/geom_linerange.html) | Vertical intervals: lines, crossbars & errorbars |
| [![](https://ggplot2.tidyverse.org/reference/icons/geom_map.png)](https://ggplot2.tidyverse.org/reference/geom_map.html) | [`geom_map()`](https://ggplot2.tidyverse.org/reference/geom_map.html) | Polygons from a reference map |
| [![](https://ggplot2.tidyverse.org/reference/icons/geom_path.png)](https://ggplot2.tidyverse.org/reference/geom_path.html) | [`geom_path()`](https://ggplot2.tidyverse.org/reference/geom_path.html) [`geom_line()`](https://ggplot2.tidyverse.org/reference/geom_path.html) [`geom_step()`](https://ggplot2.tidyverse.org/reference/geom_path.html) | Connect observations |
| [![](https://ggplot2.tidyverse.org/reference/icons/geom_point.png)](https://ggplot2.tidyverse.org/reference/geom_point.html) | [`geom_point()`](https://ggplot2.tidyverse.org/reference/geom_point.html) | Points |
| [![](https://ggplot2.tidyverse.org/reference/icons/geom_polygon.png)](https://ggplot2.tidyverse.org/reference/geom_polygon.html) | [`geom_polygon()`](https://ggplot2.tidyverse.org/reference/geom_polygon.html) | Polygons |
|  | [`geom_qq_line()`](https://ggplot2.tidyverse.org/reference/geom_qq.html) [`stat_qq_line()`](https://ggplot2.tidyverse.org/reference/geom_qq.html) [`geom_qq()`](https://ggplot2.tidyverse.org/reference/geom_qq.html) [`stat_qq()`](https://ggplot2.tidyverse.org/reference/geom_qq.html) | A quantile-quantile plot |
| [![](https://ggplot2.tidyverse.org/reference/icons/geom_quantile.png)](https://ggplot2.tidyverse.org/reference/geom_quantile.html) | [`geom_quantile()`](https://ggplot2.tidyverse.org/reference/geom_quantile.html) [`stat_quantile()`](https://ggplot2.tidyverse.org/reference/geom_quantile.html) | Quantile regression |
| [![](https://ggplot2.tidyverse.org/reference/icons/geom_ribbon.png)](https://ggplot2.tidyverse.org/reference/geom_ribbon.html) | [`geom_ribbon()`](https://ggplot2.tidyverse.org/reference/geom_ribbon.html) [`geom_area()`](https://ggplot2.tidyverse.org/reference/geom_ribbon.html) | Ribbons and area plots |
| [![](https://ggplot2.tidyverse.org/reference/icons/geom_rug.png)](https://ggplot2.tidyverse.org/reference/geom_rug.html) | [`geom_rug()`](https://ggplot2.tidyverse.org/reference/geom_rug.html) | Rug plots in the margins |
| [![](https://ggplot2.tidyverse.org/reference/icons/geom_segment.png)](https://ggplot2.tidyverse.org/reference/geom_segment.html) | [`geom_segment()`](https://ggplot2.tidyverse.org/reference/geom_segment.html) [`geom_curve()`](https://ggplot2.tidyverse.org/reference/geom_segment.html) | Line segments and curves |
| [![](https://ggplot2.tidyverse.org/reference/icons/geom_smooth.png)](https://ggplot2.tidyverse.org/reference/geom_smooth.html) | [`geom_smooth()`](https://ggplot2.tidyverse.org/reference/geom_smooth.html) [`stat_smooth()`](https://ggplot2.tidyverse.org/reference/geom_smooth.html) | Smoothed conditional means |
| [![](https://ggplot2.tidyverse.org/reference/icons/geom_spoke.png)](https://ggplot2.tidyverse.org/reference/geom_spoke.html) | [`geom_spoke()`](https://ggplot2.tidyverse.org/reference/geom_spoke.html) | Line segments parameterised by location, direction and distance |
| [![](https://ggplot2.tidyverse.org/reference/icons/geom_text.png)](https://ggplot2.tidyverse.org/reference/geom_text.html) | [`geom_label()`](https://ggplot2.tidyverse.org/reference/geom_text.html) [`geom_text()`](https://ggplot2.tidyverse.org/reference/geom_text.html) | Text |
| [![](https://ggplot2.tidyverse.org/reference/icons/geom_raster.png)](https://ggplot2.tidyverse.org/reference/geom_tile.html) | [`geom_raster()`](https://ggplot2.tidyverse.org/reference/geom_tile.html) [`geom_rect()`](https://ggplot2.tidyverse.org/reference/geom_tile.html) [`geom_tile()`](https://ggplot2.tidyverse.org/reference/geom_tile.html) | Rectangles |
| [![](https://ggplot2.tidyverse.org/reference/icons/geom_violin.png)](https://ggplot2.tidyverse.org/reference/geom_violin.html) | [`geom_violin()`](https://ggplot2.tidyverse.org/reference/geom_violin.html) [`stat_ydensity()`](https://ggplot2.tidyverse.org/reference/geom_violin.html) | Violin plot |
| [![](https://ggplot2.tidyverse.org/reference/icons/geom_sf.png)](https://ggplot2.tidyverse.org/reference/ggsf.html) | [`coord_sf()`](https://ggplot2.tidyverse.org/reference/ggsf.html) [`geom_sf()`](https://ggplot2.tidyverse.org/reference/ggsf.html) [`geom_sf_label()`](https://ggplot2.tidyverse.org/reference/ggsf.html) [`geom_sf_text()`](https://ggplot2.tidyverse.org/reference/ggsf.html) [`stat_sf()`](https://ggplot2.tidyverse.org/reference/ggsf.html) | Visualise sf objects |

### Stats

A handful of layers are more easily specified with a `stat_` function, drawing attention to the statistical transformation rather than the visual appearance. The computed variables can be mapped using [`after_stat()`](https://ggplot2.tidyverse.org/reference/aes_eval.html).

| functions | notes |
| :--- | :--- |
| [`stat_ecdf()`](https://ggplot2.tidyverse.org/reference/stat_ecdf.html) | Compute empirical cumulative distribution |
| [`stat_ellipse()`](https://ggplot2.tidyverse.org/reference/stat_ellipse.html) | Compute normal data ellipses |
| [`geom_function()`](https://ggplot2.tidyverse.org/reference/geom_function.html) [`stat_function()`](https://ggplot2.tidyverse.org/reference/geom_function.html) | Draw a function as a continuous curve |
| [`stat_identity()`](https://ggplot2.tidyverse.org/reference/stat_identity.html) | Leave data as is |
| [`stat_summary_2d()`](https://ggplot2.tidyverse.org/reference/stat_summary_2d.html) [`stat_summary_hex()`](https://ggplot2.tidyverse.org/reference/stat_summary_2d.html) | Bin and summarise in 2d \(rectangle & hexagons\) |
| [`stat_summary_bin()`](https://ggplot2.tidyverse.org/reference/stat_summary.html) [`stat_summary()`](https://ggplot2.tidyverse.org/reference/stat_summary.html) | Summarise y values at unique/binned x |
| [`stat_unique()`](https://ggplot2.tidyverse.org/reference/stat_unique.html) | Remove duplicates |
| [`stat_sf_coordinates()`](https://ggplot2.tidyverse.org/reference/stat_sf_coordinates.html) | Extract coordinates from 'sf' objects |
| [`after_stat()`](https://ggplot2.tidyverse.org/reference/aes_eval.html) [`after_scale()`](https://ggplot2.tidyverse.org/reference/aes_eval.html) [`stage()`](https://ggplot2.tidyverse.org/reference/aes_eval.html) | Control aesthetic evaluation |

### Position

 All layers have a position adjustment that resolves overlapping geoms. Override the default by using the `position` argument to the `geom_` or `stat_` function.

| shape | functions | title |
| :--- | :--- | :--- |
| [![](https://ggplot2.tidyverse.org/reference/icons/position_dodge.png)](https://ggplot2.tidyverse.org/reference/position_dodge.html) | [`position_dodge()`](https://ggplot2.tidyverse.org/reference/position_dodge.html) [`position_dodge2()`](https://ggplot2.tidyverse.org/reference/position_dodge.html) | Dodge overlapping objects side-to-side |
| [![](https://ggplot2.tidyverse.org/reference/icons/position_identity.png)](https://ggplot2.tidyverse.org/reference/position_identity.html) | [`position_identity()`](https://ggplot2.tidyverse.org/reference/position_identity.html) | Don't adjust position |
| [![](https://ggplot2.tidyverse.org/reference/icons/position_jitter.png)](https://ggplot2.tidyverse.org/reference/position_jitter.html) | [`position_jitter()`](https://ggplot2.tidyverse.org/reference/position_jitter.html) | Jitter points to avoid overplotting |
|  | [`position_jitterdodge()`](https://ggplot2.tidyverse.org/reference/position_jitterdodge.html) | Simultaneously dodge and jitter |
|  | [`position_nudge()`](https://ggplot2.tidyverse.org/reference/position_nudge.html) | Nudge points a fixed distance |
| [![](https://ggplot2.tidyverse.org/reference/icons/position_stack.png)](https://ggplot2.tidyverse.org/reference/position_stack.html) | [`position_stack()`](https://ggplot2.tidyverse.org/reference/position_stack.html) [`position_fill()`](https://ggplot2.tidyverse.org/reference/position_stack.html) | Stack overlapping objects on top of each another |

### Annotations

Annotations are a special type of layer that don’t inherit global settings from the plot. They are used to add fixed reference data to plots.

| functions | notes |
| :--- | :--- |
| [`geom_abline()`](https://ggplot2.tidyverse.org/reference/geom_abline.html) [`geom_hline()`](https://ggplot2.tidyverse.org/reference/geom_abline.html) [`geom_vline()`](https://ggplot2.tidyverse.org/reference/geom_abline.html) | Reference lines: horizontal, vertical, and diagonal |
| [`annotate()`](https://ggplot2.tidyverse.org/reference/annotate.html) | Create an annotation layer |
| [`annotation_custom()`](https://ggplot2.tidyverse.org/reference/annotation_custom.html) | Annotation: Custom grob |
| [`annotation_logticks()`](https://ggplot2.tidyverse.org/reference/annotation_logticks.html) | Annotation: log tick marks |
| [`annotation_map()`](https://ggplot2.tidyverse.org/reference/annotation_map.html) | Annotation: a maps |
| [`annotation_raster()`](https://ggplot2.tidyverse.org/reference/annotation_raster.html) | Annotation: high-performance rectangular tiling |
| [`borders()`](https://ggplot2.tidyverse.org/reference/borders.html) | Create a layer of map borders |

## Aesthetics

The following help topics give a broad overview of some of the ways you can use each aesthetic.

| functions | notes |
| :--- | :--- |
| [`aes_colour_fill_alpha`](https://ggplot2.tidyverse.org/reference/aes_colour_fill_alpha.html) | Colour related aesthetics: colour, fill, and alpha |
| [`aes_group_order`](https://ggplot2.tidyverse.org/reference/aes_group_order.html) | Aesthetics: grouping |
| [`aes_linetype_size_shape`](https://ggplot2.tidyverse.org/reference/aes_linetype_size_shape.html) | Differentiation related aesthetics: linetype, size, shape |
| [`aes_position`](https://ggplot2.tidyverse.org/reference/aes_position.html) | Position related aesthetics: x, y, xmin, xmax, ymin, ymax, xend, yend |

## Scales

Scales control the details of how data values are translated to visual properties. Override the default scales to tweak details like the axis labels or legend keys, or to use a completely different translation from data to aesthetic. [`labs()`](https://ggplot2.tidyverse.org/reference/labs.html) and [`lims()`](https://ggplot2.tidyverse.org/reference/lims.html) are convenient helpers for the most common adjustments to the labels and limits.

| shape | functions | notes |
| :--- | :--- | :--- |
|  | [`labs()`](https://ggplot2.tidyverse.org/reference/labs.html) [`xlab()`](https://ggplot2.tidyverse.org/reference/labs.html) [`ylab()`](https://ggplot2.tidyverse.org/reference/labs.html) [`ggtitle()`](https://ggplot2.tidyverse.org/reference/labs.html) | Modify axis, legend, and plot labels |
|  | [`lims()`](https://ggplot2.tidyverse.org/reference/lims.html) [`xlim()`](https://ggplot2.tidyverse.org/reference/lims.html) [`ylim()`](https://ggplot2.tidyverse.org/reference/lims.html) | Set scale limits |
|  | [`expand_limits()`](https://ggplot2.tidyverse.org/reference/expand_limits.html) | Expand the plot limits, using data |
|  | [`expansion()`](https://ggplot2.tidyverse.org/reference/expansion.html) [`expand_scale()`](https://ggplot2.tidyverse.org/reference/expansion.html) | Generate expansion vector for scales |
| [![](https://ggplot2.tidyverse.org/reference/icons/scale_alpha.png)](https://ggplot2.tidyverse.org/reference/scale_alpha.html) | [`scale_alpha()`](https://ggplot2.tidyverse.org/reference/scale_alpha.html) [`scale_alpha_continuous()`](https://ggplot2.tidyverse.org/reference/scale_alpha.html) [`scale_alpha_binned()`](https://ggplot2.tidyverse.org/reference/scale_alpha.html) [`scale_alpha_discrete()`](https://ggplot2.tidyverse.org/reference/scale_alpha.html) [`scale_alpha_ordinal()`](https://ggplot2.tidyverse.org/reference/scale_alpha.html) | Alpha transparency scales |
|  | [`scale_x_binned()`](https://ggplot2.tidyverse.org/reference/scale_binned.html) [`scale_y_binned()`](https://ggplot2.tidyverse.org/reference/scale_binned.html) | Positional scales for binning continuous data \(x & y\) |
| [![](https://ggplot2.tidyverse.org/reference/icons/scale_colour_brewer.png)](https://ggplot2.tidyverse.org/reference/scale_brewer.html) | [`scale_colour_brewer()`](https://ggplot2.tidyverse.org/reference/scale_brewer.html) [`scale_fill_brewer()`](https://ggplot2.tidyverse.org/reference/scale_brewer.html) [`scale_colour_distiller()`](https://ggplot2.tidyverse.org/reference/scale_brewer.html) [`scale_fill_distiller()`](https://ggplot2.tidyverse.org/reference/scale_brewer.html) [`scale_colour_fermenter()`](https://ggplot2.tidyverse.org/reference/scale_brewer.html) [`scale_fill_fermenter()`](https://ggplot2.tidyverse.org/reference/scale_brewer.html) | Sequential, diverging and qualitative colour scales from colorbrewer.org |
| [![](https://ggplot2.tidyverse.org/reference/icons/scale_colour_continuous.png)](https://ggplot2.tidyverse.org/reference/scale_colour_continuous.html) | [`scale_colour_continuous()`](https://ggplot2.tidyverse.org/reference/scale_colour_continuous.html) [`scale_fill_continuous()`](https://ggplot2.tidyverse.org/reference/scale_colour_continuous.html) | Continuous and binned colour scales |
|  | [`scale_colour_discrete()`](https://ggplot2.tidyverse.org/reference/scale_colour_discrete.html) [`scale_fill_discrete()`](https://ggplot2.tidyverse.org/reference/scale_colour_discrete.html) | Discrete colour scales |
|  | [`scale_x_continuous()`](https://ggplot2.tidyverse.org/reference/scale_continuous.html) [`scale_y_continuous()`](https://ggplot2.tidyverse.org/reference/scale_continuous.html) [`scale_x_log10()`](https://ggplot2.tidyverse.org/reference/scale_continuous.html) [`scale_y_log10()`](https://ggplot2.tidyverse.org/reference/scale_continuous.html) [`scale_x_reverse()`](https://ggplot2.tidyverse.org/reference/scale_continuous.html) [`scale_y_reverse()`](https://ggplot2.tidyverse.org/reference/scale_continuous.html) [`scale_x_sqrt()`](https://ggplot2.tidyverse.org/reference/scale_continuous.html) [`scale_y_sqrt()`](https://ggplot2.tidyverse.org/reference/scale_continuous.html) | Position scales for continuous data \(x & y\) |
| [![](https://ggplot2.tidyverse.org/reference/icons/scale_x_date.png)](https://ggplot2.tidyverse.org/reference/scale_date.html) | [`scale_x_date()`](https://ggplot2.tidyverse.org/reference/scale_date.html) [`scale_y_date()`](https://ggplot2.tidyverse.org/reference/scale_date.html) [`scale_x_datetime()`](https://ggplot2.tidyverse.org/reference/scale_date.html) [`scale_y_datetime()`](https://ggplot2.tidyverse.org/reference/scale_date.html) [`scale_x_time()`](https://ggplot2.tidyverse.org/reference/scale_date.html) [`scale_y_time()`](https://ggplot2.tidyverse.org/reference/scale_date.html) | Position scales for date/time data |
|  | [`scale_x_discrete()`](https://ggplot2.tidyverse.org/reference/scale_discrete.html) [`scale_y_discrete()`](https://ggplot2.tidyverse.org/reference/scale_discrete.html) | Position scales for discrete data |
| [![](https://ggplot2.tidyverse.org/reference/icons/scale_colour_gradient.png)](https://ggplot2.tidyverse.org/reference/scale_gradient.html) | [`scale_colour_gradient()`](https://ggplot2.tidyverse.org/reference/scale_gradient.html) [`scale_fill_gradient()`](https://ggplot2.tidyverse.org/reference/scale_gradient.html) [`scale_colour_gradient2()`](https://ggplot2.tidyverse.org/reference/scale_gradient.html) [`scale_fill_gradient2()`](https://ggplot2.tidyverse.org/reference/scale_gradient.html) [`scale_colour_gradientn()`](https://ggplot2.tidyverse.org/reference/scale_gradient.html) [`scale_fill_gradientn()`](https://ggplot2.tidyverse.org/reference/scale_gradient.html) | Gradient colour scales |
| [![](https://ggplot2.tidyverse.org/reference/icons/scale_colour_grey.png)](https://ggplot2.tidyverse.org/reference/scale_grey.html) | [`scale_colour_grey()`](https://ggplot2.tidyverse.org/reference/scale_grey.html) [`scale_fill_grey()`](https://ggplot2.tidyverse.org/reference/scale_grey.html) | Sequential grey colour scales |
| [![](https://ggplot2.tidyverse.org/reference/icons/scale_colour_hue.png)](https://ggplot2.tidyverse.org/reference/scale_hue.html) | [`scale_colour_hue()`](https://ggplot2.tidyverse.org/reference/scale_hue.html) [`scale_fill_hue()`](https://ggplot2.tidyverse.org/reference/scale_hue.html) | Evenly spaced colours for discrete data |
|  | [`scale_colour_identity()`](https://ggplot2.tidyverse.org/reference/scale_identity.html) [`scale_fill_identity()`](https://ggplot2.tidyverse.org/reference/scale_identity.html) [`scale_shape_identity()`](https://ggplot2.tidyverse.org/reference/scale_identity.html) [`scale_linetype_identity()`](https://ggplot2.tidyverse.org/reference/scale_identity.html) [`scale_alpha_identity()`](https://ggplot2.tidyverse.org/reference/scale_identity.html) [`scale_size_identity()`](https://ggplot2.tidyverse.org/reference/scale_identity.html) [`scale_discrete_identity()`](https://ggplot2.tidyverse.org/reference/scale_identity.html) [`scale_continuous_identity()`](https://ggplot2.tidyverse.org/reference/scale_identity.html) | Use values without scaling |
| [![](https://ggplot2.tidyverse.org/reference/icons/scale_linetype.png)](https://ggplot2.tidyverse.org/reference/scale_linetype.html) | [`scale_linetype()`](https://ggplot2.tidyverse.org/reference/scale_linetype.html) [`scale_linetype_binned()`](https://ggplot2.tidyverse.org/reference/scale_linetype.html) [`scale_linetype_continuous()`](https://ggplot2.tidyverse.org/reference/scale_linetype.html) [`scale_linetype_discrete()`](https://ggplot2.tidyverse.org/reference/scale_linetype.html) | Scale for line patterns |
| [![](https://ggplot2.tidyverse.org/reference/icons/scale_colour_manual.png)](https://ggplot2.tidyverse.org/reference/scale_manual.html) | [`scale_colour_manual()`](https://ggplot2.tidyverse.org/reference/scale_manual.html) [`scale_fill_manual()`](https://ggplot2.tidyverse.org/reference/scale_manual.html) [`scale_size_manual()`](https://ggplot2.tidyverse.org/reference/scale_manual.html) [`scale_shape_manual()`](https://ggplot2.tidyverse.org/reference/scale_manual.html) [`scale_linetype_manual()`](https://ggplot2.tidyverse.org/reference/scale_manual.html) [`scale_alpha_manual()`](https://ggplot2.tidyverse.org/reference/scale_manual.html) [`scale_discrete_manual()`](https://ggplot2.tidyverse.org/reference/scale_manual.html) | Create your own discrete scale |
| [![](https://ggplot2.tidyverse.org/reference/icons/scale_shape.png)](https://ggplot2.tidyverse.org/reference/scale_shape.html) | [`scale_shape()`](https://ggplot2.tidyverse.org/reference/scale_shape.html) [`scale_shape_binned()`](https://ggplot2.tidyverse.org/reference/scale_shape.html) | Scales for shapes, aka glyphs |
| [![](https://ggplot2.tidyverse.org/reference/icons/scale_size.png)](https://ggplot2.tidyverse.org/reference/scale_size.html) | [`scale_size()`](https://ggplot2.tidyverse.org/reference/scale_size.html) [`scale_radius()`](https://ggplot2.tidyverse.org/reference/scale_size.html) [`scale_size_binned()`](https://ggplot2.tidyverse.org/reference/scale_size.html) [`scale_size_area()`](https://ggplot2.tidyverse.org/reference/scale_size.html) [`scale_size_binned_area()`](https://ggplot2.tidyverse.org/reference/scale_size.html) | Scales for area or radius |
|  | [`scale_colour_steps()`](https://ggplot2.tidyverse.org/reference/scale_steps.html) [`scale_colour_steps2()`](https://ggplot2.tidyverse.org/reference/scale_steps.html) [`scale_colour_stepsn()`](https://ggplot2.tidyverse.org/reference/scale_steps.html) [`scale_fill_steps()`](https://ggplot2.tidyverse.org/reference/scale_steps.html) [`scale_fill_steps2()`](https://ggplot2.tidyverse.org/reference/scale_steps.html) [`scale_fill_stepsn()`](https://ggplot2.tidyverse.org/reference/scale_steps.html) | Binned gradient colour scales |
| [![](https://ggplot2.tidyverse.org/reference/icons/scale_colour_viridis_d.png)](https://ggplot2.tidyverse.org/reference/scale_viridis.html) | [`scale_colour_viridis_d()`](https://ggplot2.tidyverse.org/reference/scale_viridis.html) [`scale_fill_viridis_d()`](https://ggplot2.tidyverse.org/reference/scale_viridis.html) [`scale_colour_viridis_c()`](https://ggplot2.tidyverse.org/reference/scale_viridis.html) [`scale_fill_viridis_c()`](https://ggplot2.tidyverse.org/reference/scale_viridis.html) [`scale_colour_viridis_b()`](https://ggplot2.tidyverse.org/reference/scale_viridis.html) [`scale_fill_viridis_b()`](https://ggplot2.tidyverse.org/reference/scale_viridis.html) | Viridis colour scales from viridisLite |

## Guides: axes and legends

The guides \(the axes and legends\) help readers interpret your plots. Guides are mostly controlled via the scale \(e.g. with the `limits`, `breaks`, and `labels` arguments\), but sometimes you will need additional control over guide appearance. Use [`guides()`](https://ggplot2.tidyverse.org/reference/guides.html) or the `guide` argument to individual scales along with `guide_*()` functions.

| functions | notes |
| :--- | :--- |
| [`draw_key_point()`](https://ggplot2.tidyverse.org/reference/draw_key.html) [`draw_key_abline()`](https://ggplot2.tidyverse.org/reference/draw_key.html) [`draw_key_rect()`](https://ggplot2.tidyverse.org/reference/draw_key.html) [`draw_key_polygon()`](https://ggplot2.tidyverse.org/reference/draw_key.html) [`draw_key_blank()`](https://ggplot2.tidyverse.org/reference/draw_key.html) [`draw_key_boxplot()`](https://ggplot2.tidyverse.org/reference/draw_key.html) [`draw_key_crossbar()`](https://ggplot2.tidyverse.org/reference/draw_key.html) [`draw_key_path()`](https://ggplot2.tidyverse.org/reference/draw_key.html) [`draw_key_vpath()`](https://ggplot2.tidyverse.org/reference/draw_key.html) [`draw_key_dotplot()`](https://ggplot2.tidyverse.org/reference/draw_key.html) [`draw_key_pointrange()`](https://ggplot2.tidyverse.org/reference/draw_key.html) [`draw_key_smooth()`](https://ggplot2.tidyverse.org/reference/draw_key.html) [`draw_key_text()`](https://ggplot2.tidyverse.org/reference/draw_key.html) [`draw_key_label()`](https://ggplot2.tidyverse.org/reference/draw_key.html) [`draw_key_vline()`](https://ggplot2.tidyverse.org/reference/draw_key.html) [`draw_key_timeseries()`](https://ggplot2.tidyverse.org/reference/draw_key.html) | Key glyphs for legends |
| [`guide_colourbar()`](https://ggplot2.tidyverse.org/reference/guide_colourbar.html) [`guide_colorbar()`](https://ggplot2.tidyverse.org/reference/guide_colourbar.html) | Continuous colour bar guide |
| [`guide_legend()`](https://ggplot2.tidyverse.org/reference/guide_legend.html) | Legend guide |
| [`guide_axis()`](https://ggplot2.tidyverse.org/reference/guide_axis.html) | Axis guide |
| [`guide_bins()`](https://ggplot2.tidyverse.org/reference/guide_bins.html) | A binned version of guide\_legend |
| [`guide_coloursteps()`](https://ggplot2.tidyverse.org/reference/guide_coloursteps.html) [`guide_colorsteps()`](https://ggplot2.tidyverse.org/reference/guide_coloursteps.html) | Discretized colourbar guide |
| [`guide_none()`](https://ggplot2.tidyverse.org/reference/guide_none.html) | Empty guide |
| [`guides()`](https://ggplot2.tidyverse.org/reference/guides.html) | Set guides for each scale |
| [`sec_axis()`](https://ggplot2.tidyverse.org/reference/sec_axis.html) [`dup_axis()`](https://ggplot2.tidyverse.org/reference/sec_axis.html) [`derive()`](https://ggplot2.tidyverse.org/reference/sec_axis.html) | Specify a secondary axis |

## Facetting

Facetting generates small multiples, each displaying a different subset of the data. Facets are an alternative to aesthetics for displaying additional discrete variables.

| shape | functions  | notes |
| :--- | :--- | :--- |
| [![](https://ggplot2.tidyverse.org/reference/icons/facet_grid.png)](https://ggplot2.tidyverse.org/reference/facet_grid.html) | [`facet_grid()`](https://ggplot2.tidyverse.org/reference/facet_grid.html) | Lay out panels in a grid |
| [![](https://ggplot2.tidyverse.org/reference/icons/facet_wrap.png)](https://ggplot2.tidyverse.org/reference/facet_wrap.html) | [`facet_wrap()`](https://ggplot2.tidyverse.org/reference/facet_wrap.html) | Wrap a 1d ribbon of panels into 2d |
|  | [`vars()`](https://ggplot2.tidyverse.org/reference/vars.html) | Quote faceting variables |

### Labels

These functions provide a flexible toolkit for controlling the display of the “strip” labels on facets.

| functions | notes |
| :--- | :--- |
| [`labeller()`](https://ggplot2.tidyverse.org/reference/labeller.html) | Construct labelling specification |
| [`label_value()`](https://ggplot2.tidyverse.org/reference/labellers.html) [`label_both()`](https://ggplot2.tidyverse.org/reference/labellers.html) [`label_context()`](https://ggplot2.tidyverse.org/reference/labellers.html) [`label_parsed()`](https://ggplot2.tidyverse.org/reference/labellers.html) [`label_wrap_gen()`](https://ggplot2.tidyverse.org/reference/labellers.html) | Useful labeller functions |
| [`label_bquote()`](https://ggplot2.tidyverse.org/reference/label_bquote.html) | Label with mathematical expressions |

## Coordinates

The coordinate system determines how the `x` and `y` aesthetics combine to position elements in the plot. The default coordinate system is Cartesian \([`coord_cartesian()`](https://ggplot2.tidyverse.org/reference/coord_cartesian.html)\), which can be tweaked with [`coord_map()`](https://ggplot2.tidyverse.org/reference/coord_map.html), [`coord_fixed()`](https://ggplot2.tidyverse.org/reference/coord_fixed.html), [`coord_flip()`](https://ggplot2.tidyverse.org/reference/coord_flip.html), and [`coord_trans()`](https://ggplot2.tidyverse.org/reference/coord_trans.html), or completely replaced with [`coord_polar()`](https://ggplot2.tidyverse.org/reference/coord_polar.html).

| shape | functions | notes |
| :--- | :--- | :--- |
| [![](https://ggplot2.tidyverse.org/reference/icons/coord_cartesian.png)](https://ggplot2.tidyverse.org/reference/coord_cartesian.html) | [`coord_cartesian()`](https://ggplot2.tidyverse.org/reference/coord_cartesian.html) | Cartesian coordinates |
| [![](https://ggplot2.tidyverse.org/reference/icons/coord_fixed.png)](https://ggplot2.tidyverse.org/reference/coord_fixed.html) | [`coord_fixed()`](https://ggplot2.tidyverse.org/reference/coord_fixed.html) | Cartesian coordinates with fixed "aspect ratio" |
| [![](https://ggplot2.tidyverse.org/reference/icons/coord_flip.png)](https://ggplot2.tidyverse.org/reference/coord_flip.html) | [`coord_flip()`](https://ggplot2.tidyverse.org/reference/coord_flip.html) | Cartesian coordinates with x and y flipped |
| [![](https://ggplot2.tidyverse.org/reference/icons/coord_map.png)](https://ggplot2.tidyverse.org/reference/coord_map.html) | [`coord_map()`](https://ggplot2.tidyverse.org/reference/coord_map.html) [`coord_quickmap()`](https://ggplot2.tidyverse.org/reference/coord_map.html) | Map projections |
| [![](https://ggplot2.tidyverse.org/reference/icons/coord_polar.png)](https://ggplot2.tidyverse.org/reference/coord_polar.html) | [`coord_polar()`](https://ggplot2.tidyverse.org/reference/coord_polar.html) | Polar coordinates |
|  | [`coord_trans()`](https://ggplot2.tidyverse.org/reference/coord_trans.html) | Transformed Cartesian coordinate system |

## Themes

Themes control the display of all non-data elements of the plot. You can override all settings with a complete theme like [`theme_bw()`](https://ggplot2.tidyverse.org/reference/ggtheme.html), or choose to tweak individual settings by using [`theme()`](https://ggplot2.tidyverse.org/reference/theme.html) and the `element_` functions. Use [`theme_set()`](https://ggplot2.tidyverse.org/reference/theme_get.html) to modify the active theme, affecting all future plots.

| functions | notes |
| :--- | :--- |
| [`theme()`](https://ggplot2.tidyverse.org/reference/theme.html) | Modify components of a theme |
| [`theme_grey()`](https://ggplot2.tidyverse.org/reference/ggtheme.html) [`theme_gray()`](https://ggplot2.tidyverse.org/reference/ggtheme.html) [`theme_bw()`](https://ggplot2.tidyverse.org/reference/ggtheme.html) [`theme_linedraw()`](https://ggplot2.tidyverse.org/reference/ggtheme.html) [`theme_light()`](https://ggplot2.tidyverse.org/reference/ggtheme.html) [`theme_dark()`](https://ggplot2.tidyverse.org/reference/ggtheme.html) [`theme_minimal()`](https://ggplot2.tidyverse.org/reference/ggtheme.html) [`theme_classic()`](https://ggplot2.tidyverse.org/reference/ggtheme.html) [`theme_void()`](https://ggplot2.tidyverse.org/reference/ggtheme.html) [`theme_test()`](https://ggplot2.tidyverse.org/reference/ggtheme.html) | Complete themes |
| [`theme_get()`](https://ggplot2.tidyverse.org/reference/theme_get.html) [`theme_set()`](https://ggplot2.tidyverse.org/reference/theme_get.html) [`theme_update()`](https://ggplot2.tidyverse.org/reference/theme_get.html) [`theme_replace()`](https://ggplot2.tidyverse.org/reference/theme_get.html) [```%+replace%```](https://ggplot2.tidyverse.org/reference/theme_get.html) | Get, set, and modify the active theme |
| [`margin()`](https://ggplot2.tidyverse.org/reference/element.html) [`element_blank()`](https://ggplot2.tidyverse.org/reference/element.html) [`element_rect()`](https://ggplot2.tidyverse.org/reference/element.html) [`element_line()`](https://ggplot2.tidyverse.org/reference/element.html) [`element_text()`](https://ggplot2.tidyverse.org/reference/element.html) [`rel()`](https://ggplot2.tidyverse.org/reference/element.html) |  |

