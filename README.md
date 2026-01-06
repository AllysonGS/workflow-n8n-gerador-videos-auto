# 🎬 Vídeos Diários Personalizados para Amigos

![n8n](https://img.shields.io/badge/n8n-workflow-blue?style=flat&logo=n8n)
![Google Cloud](https://img.shields.io/badge/Google%20Cloud-AI%20Platform-orange?style=flat&logo=googlecloud)
![Status](https://img.shields.io/badge/Status-Experimental-yellow)

Um workflow do **n8n** que gera vídeos diários personalizados para enviar aos seus amigos.  
O fluxo utiliza a **API de geração de vídeos da Google AI Platform**, envia os vídeos para o Google Drive e envia automaticamente um **email com o vídeo** para cada amigo.

> Crie momentos especiais e surpreenda seus amigos com vídeos personalizados todos os dias! 🎄🎁

---

## 🔹 Funcionalidades Principais

- 🎯 **Trigger Diário:** o workflow dispara todos os dias às 8h da manhã.  
- 🎥 **Geração de Vídeos Personalizados:** mensagens personalizadas, nome do amigo e estilo cinematográfico.  
- 💾 **Upload Automático no Google Drive:** os vídeos ficam salvos e compartilháveis.  
- 📧 **Envio Automático de Email:** com link direto para assistir ao vídeo.  
- 👥 **Lista de Amigos Dinâmica:** você pode adicionar quantos amigos quiser.  
- ⏱ **Espera e Retry Inteligente:** garante que o vídeo só será enviado quando estiver pronto.  

---

## 🔹 Como Funciona o Workflow

1. **Trigger Diário 8h**: dispara o workflow automaticamente todos os dias às 08:00.  
2. **Informações API**: define Project ID, Location, Model ID e endpoint da API da Google.  
3. **Code in JavaScript**: lista os amigos que receberão os vídeos.  
4. **Separar Amigos**: divide a lista para processar cada amigo individualmente.  
5. **Preparar Dados**: cria dados específicos para cada vídeo (nome, email, URL da API).  
6. **Iniciar Geração do Vídeo**: envia requisição para a Google AI gerar o vídeo.  
7. **Aguardar Processamento / Verificar Status**: monitora a operação até o vídeo estar pronto.  
8. **Converter Base64**: transforma o vídeo retornado em `.mp4`.  
9. **Upload no Google Drive / Compartilhar Arquivo**: envia para o Drive e cria link público.  
10. **Preparar Email / Enviar Email**: envia email personalizado com o link do vídeo.  

---

## 🔹 Pré-requisitos

Antes de importar e usar o workflow, você precisa de:

1. **n8n** (versão mais recente recomendada)  
2. **Credenciais Google**:
   - **AI Platform** (OAuth2)  
   - **Google Drive** (OAuth2)  
   - **Gmail** (OAuth2)  
3. **Lista de amigos**:
   - Nome  
   - Email  
   *(configurável no node `Code in JavaScript`)*

---

## 🔹 Como Importar no n8n

1. Faça o download do arquivo do workflow: `meu_workflow.json`.  
2. No n8n, clique em **Importar Workflow → Arquivo JSON**.  
3. Atualize as **credenciais Google** nos nodes correspondentes (AI, Drive e Gmail).  
4. Ative o workflow.  

> Agora você terá vídeos diários sendo gerados e enviados automaticamente!

---

## 🔹 Personalização

Você pode ajustar facilmente:  
- Horário do trigger (node `Trigger Diário 8h`)  
- Lista de amigos (node `Code in JavaScript`)  
- Mensagens do vídeo (node `Iniciar Geração do Vídeo`)  
- Duração do vídeo, estilo e proporção (prompt e parâmetros na API)  

---

## 🔹 Estrutura do Workflow

```text
Trigger Diário 8h
      │
Informações API
      │
   Code in JS → Separar Amigos
      │
  Preparar Dados
      │
Iniciar Geração do Vídeo
      │
Aguardar Processamento → Verificar Status
      │
Vídeo Completo?
 ├── Não → Aguardar Retry → volta para Aguardar Processamento
 └── Sim → Converter Base64 → Upload no Drive → Compartilhar Arquivo → Preparar Email → Enviar Email
 
```


## 🔹 Exemplo de Email Enviado

Assunto: 🎅 Mensagem Especial de Natal para Você!

Corpo do email:

<div style="font-family: Arial, sans-serif; max-width: 600px; margin: 0 auto; padding: 20px;">
  <h2 style="color: #c41e3a;">🎄 Olá, {{ nomeAmigo }}! 🎄</h2>
  
  <p style="font-size: 16px; line-height: 1.6;">
    O Papai Noel preparou uma mensagem especial para você! 🎅✨
  </p>
  
  <p style="font-size: 16px; line-height: 1.6;">
    Clique no link abaixo para assistir seu vídeo personalizado:
  </p>
  
  <div style="text-align: center; margin: 30px 0;">
    <a href="{{ videoLink }}" 
       style="background-color: #c41e3a; color: white; padding: 15px 30px; text-decoration: none; border-radius: 5px; font-size: 18px; display: inline-block;">
      🎬 Assistir Vídeo
    </a>
  </div>
  
  <p style="font-size: 14px; color: #666; line-height: 1.6;">
    Que este Natal seja repleto de alegria, amor e momentos inesquecíveis! 🎁❤️
  </p>
  
  <hr style="border: none; border-top: 1px solid #eee; margin: 20px 0;">
  
  <p style="font-size: 12px; color: #999;">
    Mensagem enviada com carinho ❤️
  </p>
</div>

## 🔹 Dicas e Observações

- O vídeo padrão tem 8 segundos, proporção 9:16, estilo cinematográfico.
- É possível adaptar o prompt para outras ocasiões (aniversário, Páscoa, etc.).
- Workflow escala facilmente para mais amigos ou horários diferentes.
- Garantia de envio apenas quando o vídeo estiver totalmente pronto, evitando erros.

---

## 🔹 Tecnologias Utilizadas

- n8n – Automação visual
- Google AI Platform – Geração de vídeos
- Google Drive API – Upload e compartilhamento
- Gmail API – Envio de emails

---

## 🔹 Licença
MIT License © Allyson Garcia

---

Use, modifique e compartilhe, mantendo os créditos.
