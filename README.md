# target-jsonl

A [Singer](https://singer.io) target that writes data to Miso [data-api](https://api.askmiso.com).

## How to use it

The `target-miso` works together with any other [Singer Tap] to move data from sources like 
[Braintree],
[Freshdesk], and [Hubspot] to Miso data-api. First, you'll need to create jinja2 templates in the 
templates folder. The template file name should be `{stream_name}.json`, and the sample content 
could be down below.

```json
{
    "user_id": "{{ data.sso }}",
    "type": "share",
    "timestamp": "{{ data.share_date|datetime_format }}",
    "product_ids": {{ data.nid|list_of_str }},
    "context": {
        "custom_context": {
            "verb": "{{ data.verb }}",
            "asset_id": "{{ data.asset_id }}",
            "asset_title": "{{ data.asset_titla }}",
            "asset_url": "{{ data.asset_url }}",
            "domain_name": "{{ data.domain_name }}",
            "tag": "{{ data.tag }}",
            "tag_description": "{{ data.tag_description }}",
            "instructor_sso": "{{ data.instructor_sso }}",
            "shared_method": "{{ data.shared_method }}"
        }
    }
}
```
