# DocTCU — Controle de Documentos Comprobatórios
> Contrato 10/2026 · T&S · Tribunal de Contas da União

Sistema web para gestão de documentos comprobatórios de terceirizados do TCU.

## 🚀 Acesso

Após o deploy no GitHub Pages, acesse via:
```
https://<seu-usuario>.github.io/<nome-do-repositorio>/
```

## 🔐 Credenciais padrão

| Usuário    | Senha         |
|------------|---------------|
| `priscila` | `tcu@2026`    |
| `gestao`   | `gestao@2026` |
| `admin`    | `admin@2026`  |

> **Importante:** altere as senhas após o primeiro acesso editando o array `USERS` no `index.html` com novos hashes SHA-256.

### Como gerar novo hash de senha

Abra o console do navegador (`F12`) e execute:
```javascript
crypto.subtle.digest('SHA-256', new TextEncoder().encode('SuaNovaSenha'))
  .then(b => console.log(Array.from(new Uint8Array(b)).map(x=>x.toString(16).padStart(2,'0')).join('')))
```
Copie o resultado e substitua o `hash` do usuário no `index.html`.

## 📦 Deploy — passo a passo

### 1. Criar repositório no GitHub

1. Acesse [github.com/new](https://github.com/new)
2. Nome sugerido: `doctcu` (pode ser privado)
3. **Não** inicialize com README
4. Clique em **Create repository**

### 2. Subir os arquivos

```bash
# Clone ou inicialize o repositório
git init
git add .
git commit -m "feat: DocTCU v1.0"
git branch -M main
git remote add origin https://github.com/<SEU-USUARIO>/doctcu.git
git push -u origin main
```

### 3. Ativar GitHub Pages

1. No repositório: **Settings → Pages**
2. Source: **GitHub Actions**
3. Aguarde ~1 min — o deploy ocorre automaticamente

### 4. Acessar o sistema

URL gerada: `https://<seu-usuario>.github.io/doctcu/`

## 🔧 Funcionalidades

- ✅ Dashboard com KPIs e gráficos de conformidade
- ✅ Matriz de controle documental por colaborador × documento
- ✅ 71 colaboradores do Contrato 10/2026 pré-cadastrados
- ✅ Requisitos de qualificação por cargo (Especificações Técnicas TCU)
- ✅ Acompanhamento de certificações pendentes (alerta 30 dias)
- ✅ Acompanhamento de diploma pendente (alerta 6 meses)
- ✅ E-mail de cobrança com formulário Forms
- ✅ Upload e vinculação de documentos
- ✅ Detecção automática por nome de arquivo
- ✅ Importação e exportação ZIP
- ✅ Exportação Excel
- ✅ Login com senha (SHA-256)

## ⚠️ Segurança

O login é client-side (SHA-256 no navegador) — adequado para uso interno em rede corporativa. Para uso externo com dados sensíveis, recomenda-se adicionar autenticação server-side.
