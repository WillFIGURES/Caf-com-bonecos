# Documentação do Site Café com Bonecos

## Visão Geral
Este documento fornece instruções para uso, manutenção e atualização do site centralizador Café com Bonecos, desenvolvido para integrar conteúdos do canal do YouTube, Instagram e outras informações relevantes sobre colecionismo de bonecos e estátuas.

## Estrutura do Site

O site foi desenvolvido com React e TypeScript, utilizando Tailwind CSS para estilização. A estrutura principal inclui:

1. **Página Inicial (Home)**: Apresenta as principais seções do site, incluindo vídeos em destaque, próxima live, blog e integração com Instagram.

2. **Vídeos**: Exibe os vídeos do canal organizados por categorias.

3. **Agenda**: Mostra a programação de lives e eventos futuros.

4. **Blog**: Artigos e notícias sobre colecionismo.

5. **Galeria**: Fotos de coleções e eventos.

6. **Sobre**: Informações sobre o canal e equipe.

7. **Contato**: Formulário para mensagens e informações de contato.

8. **Integração com Loja**: Link direto para a loja no site willfigures.com.br.

## Tecnologias Utilizadas

- **Frontend**: React, TypeScript
- **Estilização**: Tailwind CSS
- **Roteamento**: React Router
- **Gerenciador de Pacotes**: pnpm

## Como Executar o Projeto Localmente

1. Certifique-se de ter Node.js (versão 18+) e pnpm instalados.

2. Clone o repositório ou extraia os arquivos do projeto.

3. Navegue até a pasta do projeto:
   ```
   cd cafe_com_bonecos
   ```

4. Instale as dependências:
   ```
   pnpm install
   ```

5. Execute o servidor de desenvolvimento:
   ```
   pnpm run dev
   ```

6. Acesse o site em seu navegador:
   ```
   http://localhost:5173
   ```

## Como Fazer o Build para Produção

1. Execute o comando de build:
   ```
   pnpm run build
   ```

2. Os arquivos otimizados para produção serão gerados na pasta `dist`.

3. Esses arquivos podem ser hospedados em qualquer servidor web.

## Personalização e Manutenção

### Atualização de Conteúdo

#### Vídeos em Destaque
Para atualizar os vídeos em destaque, edite o arquivo `src/App.tsx` e modifique o array `featuredVideos`.

```typescript
const featuredVideos = [
  {
    title: 'Título do Vídeo',
    thumbnail: 'URL da Miniatura',
    duration: 'Duração',
    views: 'Visualizações',
    date: 'Data',
    videoId: 'ID do Vídeo no YouTube'
  },
  // Adicione mais vídeos aqui
];
```

#### Posts do Blog
Para atualizar os posts do blog, edite o array `blogPosts` no arquivo `src/App.tsx`.

```typescript
const blogPosts = [
  {
    title: 'Título do Post',
    excerpt: 'Resumo do conteúdo',
    image: 'URL da imagem',
    date: 'Data',
    author: 'Autor',
    slug: 'url-amigavel-do-post'
  },
  // Adicione mais posts aqui
];
```

#### Próxima Live
Para atualizar as informações da próxima live, localize a seção correspondente no componente `HomePage` no arquivo `src/App.tsx`.

### Adição de Novas Páginas

1. Crie um novo componente na pasta `src/components/`.
2. Adicione a rota no componente `App.tsx` dentro do componente `Routes`.

```typescript
<Route path="/nova-pagina" element={<NovaPagina />} />
```

### Personalização Visual

- As cores principais podem ser ajustadas no arquivo `src/index.css` nas variáveis CSS.
- Os componentes de UI estão na pasta `src/components/`.

## Integrações Futuras

### Integração com YouTube API
Para implementar a integração automática com o YouTube API:

1. Obtenha uma chave de API do YouTube no Google Cloud Console.
2. Instale a biblioteca axios:
   ```
   pnpm add axios
   ```
3. Crie um serviço para buscar os vídeos mais recentes:

```typescript
// src/services/youtube.ts
import axios from 'axios';

const API_KEY = 'SUA_CHAVE_API';
const CHANNEL_ID = 'UCvskbqLQ1aPaRkNJWuxD-sQ';

export const fetchLatestVideos = async (maxResults = 10) => {
  try {
    const response = await axios.get(
      `https://www.googleapis.com/youtube/v3/search?key=${API_KEY}&channelId=${CHANNEL_ID}&part=snippet,id&order=date&maxResults=${maxResults}`
    );
    return response.data.items;
  } catch (error) {
    console.error('Erro ao buscar vídeos:', error);
    return [];
  }
};
```

### Integração com Instagram
Para implementar a integração com Instagram:

1. Considere usar a API oficial do Instagram ou serviços de terceiros como o Curator.io.
2. Siga a documentação específica do serviço escolhido para implementação.

## Suporte e Contato

Para suporte técnico ou dúvidas sobre o site, entre em contato através do email: [seu-email@exemplo.com]

## Créditos

Desenvolvido por [Seu Nome/Empresa] para o canal Café com Bonecos.

---

Última atualização: 18 de maio de 2025
