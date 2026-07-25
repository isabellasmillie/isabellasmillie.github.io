Put site images here, organized by section, e.g.:

  assets/images/art/painting-1.jpg
  assets/images/research/figure-1.png

Reference them in a page with a site-relative path:

  {{ '/assets/images/art/painting-1.jpg' | relative_url }}

Keep individual files well under GitHub's 100MB hard limit — in practice,
resize photos so the long edge is around 2000px and export as JPEG or
WebP so the whole repo stays light and pages load fast.
