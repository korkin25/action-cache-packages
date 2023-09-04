## 🚀 Release Notes

---

### 🎉 New GitHub Action: Cache Procedures from korkin25/action-cache-packages

In this release, we've introduced a new GitHub Action from `korkin25/action-cache-packages`, designed to manage caching procedures based on the cache name and date.

#### **Description**: 

- This action allows you to specify the type of cache (`packages`, `pip`, `ansible-galaxy`) and optionally set a cache ID. The action takes care of setting up the cache and refreshing it when necessary.

#### **Inputs**:

- `cache-name`: Name for cache, like `packages`, `pip`, `ansible-galaxy`. (Required)
- `cache-id`: ID for cache (defaults to current date). (Optional)

#### **Main Features**:

- Validates the `cache-name` to ensure it's one of the allowed types.
- Automatically sets a default `CACHE_ID` if one is not provided.
- Determines the cache path based on the OS and `cache-name`.
- Restores the cache using the `CACHE_ID`.
- Updates packages if cache is for packages and a cache miss occurs.
- Updates pip if cache is for pip and a cache miss occurs.
- Installs Ansible Galaxy collections if cache is for ansible-galaxy and a cache miss occurs, provided `galaxy-requirements.yml` exists.

---

### 🔧 Instructions

To utilize this action in your GitHub Actions workflow:

1. Add the action to your workflow file and specify the required `cache-name` input.
2. Optionally, you can also specify a `cache-id`.

Example:

```yaml
- name: Use Cache Procedures Action
  uses: korkin25/action-cache-packages@main
  with:
    cache-name: 'packages'
