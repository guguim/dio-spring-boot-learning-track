# 🎙️ API de Orçamento Inteligente com Spring AI

Uma API REST desenvolvida com Spring Boot e Spring AI que atua como um assistente financeiro. A aplicação recebe comandos de voz, transcreve o áudio, compreende a intenção do usuário utilizando Inteligência Artificial e executa operações reais no banco de dados através de Tool Calling.

## 🚀 O que o projeto faz
O fluxo principal da aplicação consiste em:
1. Receber um arquivo de áudio `.ogg` ou `.mp3` via endpoint REST.
2. Converter o áudio em texto (Speech-to-Text).
3. Processar o texto com LLM para identificar a intenção (ex: registrar receita, consultar saldo).
4. Executar a regra de negócio local (Tool Calling).
5. Persistir as transações financeiras.
6. Retornar uma resposta em texto e/ou áudio sumarizando a ação.

## 🛠️ Tecnologias Utilizadas
* **Java 21**
* **Spring Boot 3.x**
* **Spring AI** (Integração com LLMs, Audio Transcription, Tool Calling)
* **Maven** (Gerenciamento de dependências)
* **Banco de Dados** (H2 em memória / PostgreSQL)
* **Docker** (Para conteinerização do ambiente)

## 💡 Melhoria Implementada
Além do escopo base do desafio, foram adicionadas as seguintes evoluções:
* **Validação de Regras de Negócio no Tool Calling:** A IA agora respeita validações locais. Ao tentar registrar uma despesa maior que o saldo, a função Java barra a transação e orienta a IA a informar o usuário sobre o saldo insuficiente.
* **Categorização de Despesas:** A IA analisa o contexto da despesa ("comprei um lanche", "paguei a luz") e envia automaticamente a categoria adequada para a função de salvamento.
* **Containerização:** Criação de `Dockerfile` para subir a aplicação de forma isolada e previsível.


