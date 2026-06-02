# Extracted values for report.md

## Scenario A

| Metric | Lambda zip | Lambda container |
|---|---:|---:|
| p50 client latency (ms) | 96.75 | 98.90 |
| p95 client latency (ms) | 121.13 | 154.30 |
| p99 client latency (ms) | 178.51 | 1239.40 |
| max client latency (ms) | 178.51 | 1239.40 |
| avg handler duration from CloudWatch (ms) | 80.38 | 77.12 |
| avg init duration from CloudWatch (ms) | 642.83 | 751.95 |
| cold start count in CloudWatch file | 26 | 28 |

## Scenario B

| Environment | Concurrency | p50 (ms) | p95 (ms) | p99 (ms) | Avg (ms) | Max (ms) | Tail instability |
|---|---:|---:|---:|---:|---:|---:|---|
| EC2 | 10 | 221.18 | 292.85 | 329.43 | 220.59 | 375.58 | no |
| EC2 | 50 | 1004.00 | 1249.60 | 1332.70 | 967.20 | 1390.10 | no |
| Fargate | 10 | 1091.00 | 1490.80 | 1711.60 | 1077.20 | 2099.20 | no |
| Fargate | 50 | 5399.90 | 5898.40 | 6094.20 | 5187.70 | 6194.50 | no |
| Lambda container | 10 | 83.09 | 102.26 | 136.92 | 87.94 | 775.66 | no |
| Lambda container | 5 | 84.06 | 103.23 | 134.78 | 86.32 | 148.06 | no |
| Lambda zip | 10 | 86.46 | 105.84 | 140.05 | 89.30 | 196.43 | no |
| Lambda zip | 5 | 91.51 | 111.85 | 147.36 | 91.77 | 169.16 | no |

## Scenario C

| Environment | Concurrency | p50 (ms) | p95 (ms) | p99 (ms) | Max latency (ms) |
|---|---:|---:|---:|---:|---:|
| EC2 | 50 | 937.70 | 1144.40 | 1210.40 | 1229.90 |
| Fargate | 50 | 5115.30 | 5779.80 | 6129.50 | 6209.20 |
| Lambda container | 10 | 93.30 | 1052.00 | 1245.40 | 1282.70 |
| Lambda zip | 10 | 97.70 | 1301.80 | 1462.80 | 1559.50 |

## CloudWatch

| Variant | REPORT count | Cold start count | Avg handler duration (ms) | Avg init duration (ms) |
|---|---:|---:|---:|---:|
| Lambda zip | 1291 | 26 | 80.38 | 642.83 |
| Lambda container | 1291 | 28 | 77.12 | 751.95 |

## Cost model

- Requests per month: 8,370,000
- Lambda duration used: 0.0804 s
- Lambda request cost: 1.6740 USD
- Lambda compute cost: 5.6064 USD
- Lambda total monthly cost: 7.2804 USD
- Fargate hourly cost: 0.024685 USD
- Fargate monthly cost: 17.7732 USD
- EC2 t3.small hourly cost: 0.0208 USD
- EC2 monthly cost: 14.9760 USD
- Lambda/Fargate break-even RPS: 7.88
