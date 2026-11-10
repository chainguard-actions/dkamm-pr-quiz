<!-- markdownlint-disable -->

# Hardening Report: dkamm--pr-quiz/v0.1.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `374911c4be584df24e6da57af2d990570ef0f859`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **dkamm--pr-quiz/v0.1.0** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Composite action step uses a mutable tag reference instead of a full 40-character commit SHA: `uses: actions/setup-node@v4`.

Locations:

- `action.yml:61`

### prior-fix (severity: high)

Carried forward from this version's previous harden, which fixed it; fix it again unless the code no longer has the problem. The previous harden changed action.yml without recording a finding for it, and this analysis reported nothing there. Re-apply its security changes unless the code no longer needs them. The previous patch:
```diff
diff --git a/action.yml b/action.yml
index 2c5bb9f..00c5f2c 100644
--- a/action.yml
+++ b/action.yml
@@ -1,12 +1,9 @@
 name: PR Quiz
-description:
-  A GitHub Action that uses AI to generate a quiz based on a pull request
+description: A GitHub Action that uses AI to generate a quiz based on a pull request
 author: dkamm
-
 branding:
   icon: cpu
   color: blue
-
 inputs:
   github-token:
     description: GitHub token for API access
@@ -18,47 +15,50 @@ inputs:
     description: The ngrok authtoken to use for the server hosting the quiz.
     required: true
   model:
-    description:
-      The model to use for generating the quiz.  It must be a model that
-      supports structured outputs. Defaults to 'o4-mini'.
+    description: The model to use for generating the quiz.  It must be a model that supports structured outputs. Defaults to 'o4-mini'.
     required: false
     default: 'o4-mini'
   lines-changed-threshold:
-    description:
-      The minimum number of lines changed required to create a quiz. This is to
-      prevent quizzes from being created for small pull requests.
+    description: The minimum number of lines changed required to create a quiz. This is to prevent quizzes from being created for small pull requests.
     required: false
     default: '100'
   time-limit-minutes:
-    description:
-      The time limit to complete the quiz in minutes. This prevents the action
-      from running indefinitely.
+    description: The time limit to complete the quiz in minutes. This prevents the action from running indefinitely.
     required: false
     default: '10'
   max-attempts:
-    description:
-      The maximum number of attempts to pass the quiz. A value of 0 means
-      unlimited attempts.
+    description: The maximum number of attempts to pass the quiz. A value of 0 means unlimited attempts.
     required: false
     default: '3'
   exclude-file-patterns:
-    description:
-      A list of file patterns to exclude from the quiz as a JSON-ified string.
+    description: A list of file patterns to exclude from the quiz as a JSON-ified string.
     required: false
-    default:
-      '["**/*-lock.json", "**/*-lock.yaml", "**/*.lock", "**/*.map",
-      "**/*.pb.*", "**/*_pb2.py", "**/*.generated.*", "**/*.auto.*"]'
+    default: '["**/*-lock.json", "**/*-lock.yaml", "**/*.lock", "**/*.map", "**/*.pb.*", "**/*_pb2.py", "**/*.generated.*", "**/*.auto.*"]'
   system-prompt:
-    description:
-      Optional override for the system prompt. Be sure the specify that multiple
-      choice questions must be returned.
+    description: Optional override for the system prompt. Be sure the specify that multiple choice questions must be returned.
     required: false
-
 runs:
   using: composite
   steps:
     - name: Setup Node.js
       uses: actions/setup-node@v4
       with:
         node-version: '20'
     - name: Install external dependencies

```

Locations:

- `action.yml`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, prior-fix

**Notes:**

Pinned actions/setup-node@v4 to 49933ea5288caeca8642d1e84afbd3f7d6820020 (# v4) in action.yml. The previous harden's visible diff otherwise only collapsed multi-line descriptions and removed blank lines, which are cosmetic. The only security change it needed re-applied is this pin. Inputs are already passed through env:, so there is no script injection.

