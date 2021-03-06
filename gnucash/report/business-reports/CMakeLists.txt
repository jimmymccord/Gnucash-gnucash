add_subdirectory (test)

set (business_reports_SCHEME
  aging.scm
  customer-summary.scm
  easy-invoice.scm
  fancy-invoice.scm
  taxinvoice.scm
  receipt.scm
  invoice.scm
  job-report.scm
  owner-report.scm
  payables.scm
  receivables.scm
  balsheet-eg.scm
  business-reports.scm
)

set(business_reports_DATA
  taxinvoice.eguile.scm
  taxinvoice.css
  receipt.eguile.scm
  receipt.css
  balsheet-eg.css
  balsheet-eg.eguile.scm
)

set(GUILE_OUTPUT_DIR   gnucash/report)
set(GUILE_DEPENDS
  gncmod-html
  scm-app-utils
  scm-gettext
  scm-gnc-module
  scm-engine
  scm-scm
  scm-business-reports-links
  scm-standard-reports
  scm-report-system
  )

gnc_add_scheme_targets(scm-business-reports
  "${business_reports_SCHEME}"
  ${GUILE_OUTPUT_DIR}
  "${GUILE_DEPENDS}"
  TRUE
)

install(FILES ${business_reports_DATA} DESTINATION ${SCHEME_INSTALLED_SOURCE_DIR}/gnucash/report)

set_dist_list(business_reports_DIST CMakeLists.txt ${business_reports_SCHEME} ${business_reports_DATA})
