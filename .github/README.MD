# Storage Admin - Full access to Cloud Storage buckets
resource "google_project_iam_member" "storage_admin" {
  count   = var.enable_workload_identity ? 1 : 0
  project = var.project_id
  role    = "roles/storage.admin"
  member  = "serviceAccount:${google_service_account.workload_identity[0].email}"
}
