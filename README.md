# 🍽️ Cardápios Digitais

Aplicativo mobile moderno e elegante para criação e publicação de cardápios digitais.

## ✨ Características

- ✅ Criação e gestão de até 30 cardápios por usuário
- ✅ Autenticação segura com Supabase Auth
- ✅ Upload de imagens para itens do cardápio
- ✅ URLs amigáveis geradas automaticamente
- ✅ Controle de status: Publicado ou Rascunho
- ✅ Controle de visibilidade por item
- ✅ Interface mobile-first e responsiva
- ✅ Design moderno e minimalista
- ✅ Operações CRUD completas (Criar, Ler, Atualizar, Deletar)
- ✅ Duplicação de cardápios e itens
- ✅ Visualização pública elegante

## 🛠️ Stack Tecnológica

- **Frontend**: Next.js 14+ (App Router) + React + TypeScript
- **Estilização**: Tailwind CSS
- **Backend**: Next.js API Routes
- **Autenticação**: Supabase Auth
- **Banco de Dados**: Supabase PostgreSQL
- **Armazenamento**: Supabase Storage
- **Deploy**: Vercel

## 🏛️ Arquitetura do Banco de Dados

### Tabelas Principais

**profiles** - Perfis de usuários
```sql
id (UUID, PK)
email (TEXT)
full_name (TEXT)
created_at (TIMESTAMP)
updated_at (TIMESTAMP)
```

**menus** - Cardápios
```sql
id (UUID, PK)
user_id (UUID, FK -> profiles)
name (TEXT)
slug (TEXT, UNIQUE)
status (TEXT: 'published' | 'draft')
created_at (TIMESTAMP)
updated_at (TIMESTAMP)
```

**menu_items** - Itens do cardápio
```sql
id (UUID, PK)
menu_id (UUID, FK -> menus)
name (TEXT)
description (TEXT)
price (DECIMAL)
image_url (TEXT)
is_visible (BOOLEAN)
order_position (INTEGER)
created_at (TIMESTAMP)
updated_at (TIMESTAMP)
```

## 🚀 Começando

### Pré-requisitos

- Node.js 18+ instalado
- Conta no Supabase (gratuito)
- Conta no Vercel (gratuito)

### Instalação

1. Clone o repositório:
```bash
git clone https://github.com/ridolfiweb1/cardapios-digitais.git
cd cardapios-digitais
```

2. Instale as dependências:
```bash
npm install
```

3. Configure as variáveis de ambiente:

Crie um arquivo `.env.local` na raiz do projeto:
```env
NEXT_PUBLIC_SUPABASE_URL=sua-url-do-supabase
NEXT_PUBLIC_SUPABASE_ANON_KEY=sua-chave-anonima
SUPABASE_SERVICE_ROLE_KEY=sua-chave-service-role
```

4. Execute as migrações do banco de dados no Supabase SQL Editor:

Veja o arquivo `supabase/migrations/001_initial_schema.sql`

5. Inicie o servidor de desenvolvimento:
```bash
npm run dev
```

6. Acesse http://localhost:3000

## 📝 Estrutura do Projeto

```
app/
├── (auth)/              # Rotas de autenticação
│   ├── login/
│   └── signup/
├── (dashboard)/         # Rotas protegidas
│   ├── dashboard/
│   └── menus/
├── cardapio/            # Visualização pública
│   └── [slug]/
└── api/                 # API Routes

components/
├── ui/                  # Componentes base reutilizáveis
├── auth/                # Componentes de autenticação
├── dashboard/           # Componentes do dashboard
└── menu/                # Componentes de cardápio

lib/
├── supabase/            # Configuração do Supabase
├── utils/               # Funções utilitárias
└── hooks/               # Custom hooks
```

## 🎨 Design System

### Paleta de Cores
- **Primário**: #2563eb (Azul moderno)
- **Sucesso**: #10b981 (Verde)
- **Perigo**: #ef4444 (Vermelho)
- **Cinza**: #64748b

### Tipografia
- **Fonte**: Inter (Google Fonts)
- **Tamanhos**: 14px base, 16px corpo, 20-32px headings

### Componentes
- Botões arredondados (border-radius: 8-12px)
- Cards com sombra suave
- Transições suaves (200ms)
- Espaçamento consistente (múltiplos de 4px)

## 🔐 Segurança

- Autenticação via Supabase Auth
- Row Level Security (RLS) no banco de dados
- Rotas protegidas com middleware
- Validação de permissões por usuário
- Cardápios publicados são públicos via slug

## 📦 Deploy

### Vercel (Recomendado)

1. Faça push do código para o GitHub
2. Importe o projeto no Vercel
3. Configure as variáveis de ambiente
4. Deploy automático a cada push

### Variáveis de Ambiente (Vercel)

```
NEXT_PUBLIC_SUPABASE_URL
NEXT_PUBLIC_SUPABASE_ANON_KEY
SUPABASE_SERVICE_ROLE_KEY
```

## 📚 Funcionalidades

### Autenticação
- Cadastro de novos usuários
- Login seguro
- Recuperação de senha
- Sessão persistente

### Gestão de Cardápios
- Criar até 30 cardápios
- Editar nome e status
- Duplicar cardápios
- Excluir cardápios
- Alternar entre publicado/rascunho
- URL amigável única gerada automaticamente

### Gestão de Itens
- Adicionar itens com foto, nome, descrição e preço
- Editar itens existentes
- Duplicar itens
- Excluir itens
- Controlar visibilidade (olho)
- Reordenar itens (drag-and-drop)

### Visualização Pública
- Layout responsivo e elegante
- Otimizado para mobile
- Carregamento rápido de imagens
- SEO-friendly
- Compartilhamento via URL

## 🛣️ Roadmap

- [ ] Categorias de itens
- [ ] Temas personalizados
- [ ] QR Code gerado automaticamente
- [ ] Análise de visualizações
- [ ] Modo escuro
- [ ] Múltiplos idiomas
- [ ] Export PDF
- [ ] Integração com WhatsApp

## 👥 Contribuindo

Contribuições são bem-vindas! Sinta-se à vontade para abrir issues e pull requests.

## 📝 Licença

MIT License - veja o arquivo LICENSE para mais detalhes.

## 👨‍💻 Autor

Desenvolvido por [Ridolfi Web](https://ridolfiweb.com)

---

**Feito com ❤️ e Next.js**
