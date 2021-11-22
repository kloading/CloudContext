# Dassana IaC
Supercharge your DevSecOps teams using [Dassana](https://github.com/dassana-io/dassana) to get to production faster

## Example usage
```yaml
on: [pull_request]

jobs:
  dassana-job:
    runs-on: ubuntu-latest
    name: dassana-action
    steps:
      - name: Checkout Repo
        uses: actions/checkout@v2
      - name: Install Python
        uses: actions/setup-python@v2.2.2
        with: 
          python-version: 3.8
      - name: Run Dassana IaC Action
        uses: kloading/CloudContext@main
        with:
          aws_region: 'us-west-2'
          bucket_name: 'cft-gh'
          stack_name: 'boss-test'
          template_file: 'template.yaml'
        env:
          GITHUB_PR: ${{ github.event.number }}
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
          AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          API_GATEWAY_ENDPOINT: ${{ secrets.API_GATEWAY_ENDPOINT }}
          API_KEY: ${{ secrets.API_KEY }}
```
