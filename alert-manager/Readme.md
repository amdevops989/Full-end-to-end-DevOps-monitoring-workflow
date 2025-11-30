kubectl -n monitoring create secret generic alertmanager-slack \
  --from-literal=webhook='https://hooks.slack.com/services/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'


cat /etc/alertmanager/config_out/alertmanager.env.yaml
