# nginx-vod-module status scraper

A small service to scrape [stats](https://github.com/kaltura/nginx-vod-module#vod_status)
from a [nginx-vod-module](https://github.com/kaltura/nginx-vod-module) deployment running inside 
a kubernetes cluster.

The code assumes it's being run inside a kubernetes cluster and sets up [client-go](https://github.com/kubernetes/client-go) 
to use an in-cluster config. The scraper also supports a k8s config loading from a kubeconfig file. The scraper discovers
pods by namespace and addresses them by their internal cluster IP.

Run locally with:
```
make run
```

By default, this code scrapes all discovered pods every minute. Example log line:

```json
{
  "level": "info",
  "svc": "vodmodule-stats",
  "namespace": "some-ns",
  "status_path": "/status",
  "scrapeInterval": "1m0s",
  "status_url": "http://10.0.122.100/status",
  "name": "otfp-dev-6692853f85-vrz5z",
  "c_metadata_store_ok": 118,
  "c_metadata_store_bytes": 19498366,
  "c_metadata_store_err": 0,
  "c_metadata_store_exists": 176,
  "c_metadata_fetch_hit": 14271,
  "c_metadata_fetch_bytes": 3850458896,
  "c_metadata_fetch_miss": 7410,
  "c_metadata_evicted": 0,
  "c_metadata_evicted_bytes": 0,
  "c_metadata_reset": 0,
  "c_metadata_entries": 118,
  "c_metadata_data_size": 19499472,
  "c_response_store_ok": 188,
  "c_response_store_bytes": 191044,
  "c_response_store_err": 0,
  "c_response_store_exists": 0,
  "c_response_fetch_hit": 1,
  "c_response_fetch_bytes": 3549,
  "c_response_fetch_miss": 188,
  "c_response_evicted": 0,
  "c_response_evicted_bytes": 0,
  "c_response_reset": 0,
  "c_response_entries": 188,
  "c_response_data_size": 192864,
  "c_mapping_store_ok": 10,
  "c_mapping_store_bytes": 70769,
  "c_mapping_store_err": 0,
  "c_mapping_store_exists": 0,
  "c_mapping_fetch_hit": 21645,
  "c_mapping_fetch_bytes": 820957289,
  "c_mapping_fetch_miss": 10,
  "c_mapping_evicted": 0,
  "c_mapping_evicted_bytes": 0,
  "c_mapping_reset": 0,
  "c_mapping_entries": 10,
  "c_mapping_data_size": 70816,
  "c_drm_info_store_ok": 1,
  "c_drm_info_store_bytes": 1278,
  "c_drm_info_store_err": 0,
  "c_drm_info_store_exists": 0,
  "c_drm_info_fetch_hit": 1,
  "c_drm_info_fetch_bytes": 1278,
  "c_drm_info_fetch_miss": 1,
  "c_drm_info_evicted": 0,
  "c_drm_info_evicted_bytes": 0,
  "c_drm_info_reset": 0,
  "c_drm_info_entries": 1,
  "c_drm_info_data_size": 1280,
  "pc_map_path_sum": 8298,
  "pc_map_path_count": 10,
  "pc_map_path_max": 2458,
  "pc_map_path_max_time": 1589739481,
  "pc_map_path_max_pid": 7,
  "pc_build_manifest_sum": 1425,
  "pc_build_manifest_count": 188,
  "pc_build_manifest_max": 257,
  "pc_build_manifest_max_time": 1589739568,
  "pc_build_manifest_max_pid": 108,
  "pc_init_frame_prod_sum": 270049,
  "pc_init_frame_prod_count": 14351,
  "pc_init_frame_prod_max": 13862,
  "pc_init_frame_prod_max_time": 1589752859,
  "pc_init_frame_prod_max_pid": 10965,
  "pc_total_sum": 7286245578,
  "pc_total_count": 3948,
  "pc_total_max": 14439759,
  "pc_total_max_time": 1589756577,
  "pc_total_max_pid": 19525,
  "pc_store_cache_sum": 19187,
  "pc_store_cache_count": 493,
  "pc_store_cache_max": 623,
  "pc_store_cache_max_time": 1589751241,
  "pc_store_cache_max_pid": 9777,
  "pc_get_drm_info_sum": 41514,
  "pc_get_drm_info_count": 1,
  "pc_get_drm_info_max": 41514,
  "pc_get_drm_info_max_time": 1589739730,
  "pc_get_drm_info_max_pid": 372,
  "pc_read_file_sum": 0,
  "pc_read_file_count": 0,
  "pc_read_file_max": 0,
  "pc_read_file_max_time": 0,
  "pc_read_file_max_pid": 0,
  "pc_proc_frames_sum": 4055919,
  "pc_proc_frames_count": 30935,
  "pc_proc_frames_max": 9486,
  "pc_proc_frames_max_time": 1589743253,
  "pc_proc_frames_max_pid": 9711,
  "pc_fetch_cache_sum": 36312,
  "pc_fetch_cache_count": 43527,
  "pc_fetch_cache_max": 4096,
  "pc_fetch_cache_max_time": 1589753498,
  "pc_fetch_cache_max_pid": 12991,
  "pc_async_read_file_sum": 21313982582,
  "pc_async_read_file_count": 24816,
  "pc_async_read_file_max": 10013588,
  "pc_async_read_file_max_time": 1589742490,
  "pc_async_read_file_max_pid": 5685,
  "pc_media_parse_sum": 580394,
  "pc_media_parse_count": 14565,
  "pc_media_parse_max": 33507,
  "pc_media_parse_max_time": 1589739861,
  "pc_media_parse_max_pid": 801,
  "pc_open_file_sum": 0,
  "pc_open_file_count": 0,
  "pc_open_file_max": 0,
  "pc_open_file_max_time": 0,
  "pc_open_file_max_pid": 0,
  "pc_async_open_file_sum": 0,
  "pc_async_open_file_count": 0,
  "pc_async_open_file_max": 0,
  "pc_async_open_file_max_time": 0,
  "pc_async_open_file_max_pid": 0,
  "pc_parse_media_set_sum": 4287076,
  "pc_parse_media_set_count": 21655,
  "pc_parse_media_set_max": 30684,
  "pc_parse_media_set_max_time": 1589742350,
  "pc_parse_media_set_max_pid": 4794,
  "time": "2020-05-17T19:18:34-04:00",
  "message": "successful scrape"
}
```