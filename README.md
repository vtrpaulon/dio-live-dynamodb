# dio-live-dynamodb

# Criar uma tabela
aws dynamodb create-table \
    --table-name Pessoas \
    --attribute-definitions \
        AttributeName=Nome,AttributeType=S \
        AttributeName=SobreNome,AttributeType=S \
    --key-schema \
        AttributeName=Nome,KeyType=HASH \
        AttributeName=SobreNome,KeyType=RANGE \
    --provisioned-throughput \
        ReadCapacityUnits=10,WriteCapacityUnits=5

# Inserir um item
aws dynamodb put-item \
    --table-name Music \
    --item file://itemPessoa.json \

# Inserir múltiplos itens
aws dynamodb batch-write-item \
    --request-items file://batchPessoas.json