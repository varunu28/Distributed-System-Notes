# Consistent Hashing

#### Examples 
 - Cassandra
 - AWS DynamoDb

#### Formula for checking consistency 
```
R + W > N

R - Number of replicas that agree on read (Read quoram)
W - Number of replicas that acknowledge an update (Write quoram)
N - Number of replicas
```
The formula does not hold in scenario where we prefer low latency over consistency.
