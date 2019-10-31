```bash
# build docker images
cd prometheus/golang
CGO_ENABLED=0 GOOS=linux go build -v

docker build . -t prometheus-golang
cd ../..
docker-compose stop && docker-compose rm -f && docker-compose up -d
```

- 统计组件

  - jenkins
    - jenkins_step_counter: project_name, branch, stage, step, status(success/fail/cancelled)
    - jenkins_project_counter: project_name, branch, status(success/fail/cancelled)
    - jenkins_step_duration: project_name, branch, stage, step, status(success/fail/cancelled)
    - jenkins_project_duration: project_name, branch, status(success/fail/cancelled)
  - gitlab
    - gitlab_commit_changes_counter: project_name, ref, commit_id, commit_email, change_type(added/modified/removed)
  - jira
    - jira_issue_updates_counter: project_name, issue_key, update_type(worklog, comment)
  - sonarqube
    - sonarqube_quality_gate_counter: project_name, module_name, metric(new_security_rating/new_reliability_rating/new_maintainability_rating/new_coverage)
  - harbor
  - nexus
    - nexus_repo_assets_upload_counter: repo_name, format
  - kubernetes

- 统计维度

  - 次数
  - 错误率
  - 时长


git diff c31cf6d80df85d6112812fed74214bc036bde3d4 20874a62b279903573ad980b869d77d33e6f4b81 --shortstat

```bash
# 使用kind创建集群
kind create cluster --image kindest/node:v1.16.2 --config kind.yaml

# 向kind的node节点load docker-image
kind load docker-image nginx:latest
# 创建nginx服务
kubectl run nginx --image=nginx:latest --port=80 --replicas=2 --image-pull-policy=IfNotPresent --labels=app=nginx
kubectl create service nodeport nginx --tcp=80:80 --node-port=30000
# 测试服务
curl http://localhost:30000

# 创建alpine服务
kind load docker-image alpine:edge
kubectl run alpine --image=alpine:edge --image-pull-policy=IfNotPresent --command -- tail -f /dev/null
```
