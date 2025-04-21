# merge-policy-enforcer.sh

A small Bash utility that **bulk‑configures all projects** in your GitLab instance to:

- **Enforce fast‑forward only** merges (no merge commits)
- **Encourage squash** by default on Merge Requests
- Apply your **custom squash‑commit message template**:
```
%{title}

%{description}

See merge request !%{reference}
```


---

## Features

- **Pagination‑aware:** walks through every page of projects via the GitLab REST API  
- **Idempotent:** safe to re‑run anytime; skips or updates projects as needed  
- **Customizable endpoint:** override your API URL (e.g. `https://gitlab.example.com/api/v4`)  
- **Secure:** reads a Personal Access Token at startup (no hard‑coding)  

---

## Prerequisites

- `bash`, `curl`, `jq`  
- A GitLab Personal Access Token with `api` scope  

---

## Usage

```bash
# adjust permissions once
chmod +x merge-policy-enforcer.sh

# then just run it:
./merge-policy-enforcer.sh
```
You’ll be prompted for your GitLab API URL and token, and then the script will loop through every project, applying your fast‑forward + squash policies in one go.
