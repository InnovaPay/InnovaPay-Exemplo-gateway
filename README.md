Este projeto demonstra como integrar o Gateway de Pagamento da InnovaPay África em aplicações web ou sistemas backend, permitindo processar pagamentos de forma rápida, segura e eficiente.

📌 Funcionalidades
💳 Processamento de pagamentos online
🔐 Autenticação segura via API Key
📡 Integração com backend (REST API)
⚡ Respostas em tempo real
🧾 Geração de referência de pagamento
📲 Suporte para múltiplos métodos (cartão, transferência, QR Code)
🛠️ Requisitos

Antes de começar, certifique-se de ter instalado:

Node.js (v16 ou superior)
npm ou yarn
Conta ativa na InnovaPay África
API Key válida
📦 Instalação
# Clonar o repositório
git clone https://github.com/seu-usuario/InnovaPay-Exemplo-gateway.git

# Entrar no diretório
cd InnovaPay-Exemplo-gateway

# Instalar dependências
npm install
⚙️ Configuração

Crie um arquivo .env na raiz do projeto:

INNOVAPAY_API_KEY=your_api_key_here
INNOVAPAY_BASE_URL=https://api.innovapayafrica.com
🚀 Como usar
1. Criar um pagamento
const axios = require("axios");

async function criarPagamento() {
  const response = await axios.post(
    `${process.env.INNOVAPAY_BASE_URL}/payments`,
    {
      amount: 10000,
      currency: "AOA",
      description: "Pagamento de teste",
      customer: {
        name: "Cliente Teste",
        email: "cliente@email.com"
      }
    },
    {
      headers: {
        Authorization: `Bearer ${process.env.INNOVAPAY_API_KEY}`
      }
    }
  );

  console.log(response.data);
}

criarPagamento();
2. Verificar status do pagamento
async function verificarPagamento(paymentId) {
  const response = await axios.get(
    `${process.env.INNOVAPAY_BASE_URL}/payments/${paymentId}`,
    {
      headers: {
        Authorization: `Bearer ${process.env.INNOVAPAY_API_KEY}`
      }
    }
  );

  console.log(response.data);
}
🔄 Webhooks (Opcional)

A InnovaPay pode enviar notificações automáticas sobre o estado dos pagamentos.

Exemplo:
app.post("/webhook", (req, res) => {
  const evento = req.body;

  if (evento.status === "success") {
    console.log("Pagamento confirmado");
  }

  res.sendStatus(200);
});
🔐 Segurança
Nunca exponha sua API Key no frontend
Utilize HTTPS em produção
Valide sempre os dados recebidos
Implemente autenticação e controle de acesso
🧪 Ambiente de Teste

Utilize credenciais de sandbox para testes:

INNOVAPAY_BASE_URL=https://sandbox.api.innovapayafrica.com
📞 Suporte

Se precisar de ajuda:

📧 geral@innovatekno.com

🌐 https://pay.innovatekno.com

📄 Licença

Este projeto é apenas para fins de demonstração e integração com a plataforma InnovaPay.
