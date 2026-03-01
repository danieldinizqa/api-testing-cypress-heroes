# 🛡️ API Testing - Cypress Heroes Case

Este projeto demonstra a validação da camada de Backend da aplicação **Cypress Heroes**, utilizando o **Postman** para testes manuais e automatizados de integração.

## 🧠 Desafios e Troubleshooting (O que eu resolvi)

O foco deste projeto foi solucionar divergências técnicas entre a interface e o contrato da API:

* **Autenticação JWT:** Implementação de script `Post-response` para captura automática do `access_token` no ambiente.
* **Divergência de Payload (401):** Identificação de que o servidor exige a chave `username` via DTO, apesar do label frontal "Email".
* **Resolução de Erro 500 (Map/Prisma):** Debugging via log do servidor para ajustar o campo `powers` de String para um **Array de Inteiros**, garantindo a integridade com o Prisma ORM.

## 🛠️ Como rodar os testes
1. Importe a collection `test Herores.postman_environment.json` e o environment `teste Heroes API.postman_collection.json` no Postman.
2. Certifique-se de que o backend local está em `http://localhost:3001`.
3. Execute o request de **Login** para atualizar o token automaticamente.
4. Teste os fluxos de **Criação** e **Exclusão** de heróis.
