# Karaokê · Spotify

App web (um único arquivo, `index.html`) que se conecta à sua conta do Spotify, busca músicas no catálogo e abre um "palco" de karaokê com a letra sincronizada linha por linha.

## O que ele faz

- **Busca própria** no catálogo do Spotify (por música, artista ou álbum), com "carregar mais".
- **Palco de karaokê**: a letra rola sozinha, a frase atual vai sendo pintada de dourado, com contagem regressiva antes de cada entrada. Também tem tela cheia e a tela não apaga.
- **Versão sem voz**: procura no Spotify versões *karaokê* e *instrumentais* da mesma música e troca com um toque. A letra continua a da original.
- **Ajuste de sincronia**: botões −/+ (0,25 s) e **"Marcar 1ª frase"**: você toca no instante em que a primeira frase deve começar e o app alinha tudo. O ajuste fica salvo para cada música.
- **Onde tocar**: direto no navegador do computador (Web Playback SDK) **ou** controlando o app do Spotify no celular, na TV ou numa caixa de som (Spotify Connect). No celular, o som sai pelo app do Spotify e a letra aparece aqui.
- **"Tocando agora"**: abre o palco com a música que você já está ouvindo no Spotify. Se você trocar de faixa pelo app do Spotify, o palco acompanha.
- **Letra própria**: dá para colar uma letra em formato LRC quando a automática não existir.
- **Sincronizar no toque**: quando a letra vem sem os tempos, toque em "⏱ Sincronizar letra". A música recomeça e você toca em "Começou!" a cada frase. A letra sincronizada fica salva para as próximas vezes.

## Modo festa e pontuação

- **🏆 Festa**: cadastre os participantes. Ao escolher uma música, o app pergunta "Quem vai cantar?" e destaca de quem é a vez (quem está há mais tempo sem cantar).
- **Nota ao vivo pelo microfone**: aparecem a nota musical que você está cantando, uma trilha da sua voz, "Perfeito!/Ótimo!/Bom!" a cada frase e um combo de frases seguidas.
- **Nota final de 0 a 100**, com estrelas e quatro critérios:
  - **Ritmo**: cantou nas frases certas, na hora certa (é o que mais pesa).
  - **Afinação**: as notas caem certinho nos semitons, sem ficar "entre" notas.
  - **Tom**: as notas ficam dentro de uma mesma escala musical.
  - **Expressão**: variação de intensidade, ou seja, se não cantou tudo no mesmo volume.
- **👏 Aplausômetro**: depois da nota, a plateia aplaude e grita por 5 s e vale até +10 pontos.
- **Ranking**: melhor nota, média e número de músicas por participante, além das últimas apresentações. Fica salvo no navegador.

Como não existe a melodia oficial de cada música para comparar, a nota mede ritmo, afinação e consistência do cantor, e não "igualdade com o cantor original". Para funcionar bem, deixe a música tocando numa caixa de som ou TV e o celular perto de quem canta.

O **modo demonstração** funciona sem Spotify, com áudio sintetizado, e serve para testar o palco e a pontuação.

Atalhos no computador: `espaço` toca/pausa, `←`/`→` voltam/avançam 5 s, `[`/`]` ajustam a sincronia, `F` liga a tela cheia e `Esc` sai do palco.

## Requisitos

- Conta **Spotify Premium**. Desde fevereiro de 2026, o Spotify exige Premium do dono do app em modo de desenvolvimento, e tocar/controlar a reprodução também exige Premium.
- Navegador moderno (Chrome, Edge ou Firefox no computador). No celular, o navegador **não** toca o Spotify sozinho, então escolha o seu celular (app do Spotify) como aparelho no palco.

## Configuração (uma vez só)

### 1. Escolha onde o app vai rodar

O Spotify só aceita endereços `https://` ou `http://127.0.0.1` (o endereço `localhost` **não** é aceito).

**Opção A: no seu computador (mais rápido para testar)**

```bash
cd pasta-do-karaoke
python -m http.server 8888 --bind 127.0.0.1
```

Depois, abra `http://127.0.0.1:8888/` no navegador.

**Opção B: GitHub Pages (grátis, com https, funciona no celular e na TV)**

1. Crie um repositório no GitHub e envie o `index.html`.
2. Em *Settings → Pages*, publique a branch `main`.
3. O endereço vai ser algo como `https://seu-usuario.github.io/karaoke/`.

Netlify, Vercel ou Cloudflare Pages também servem, porque qualquer hospedagem estática com https funciona.

### 2. Crie o app no Spotify

1. Acesse <https://developer.spotify.com/dashboard> e clique em **Create app**.
2. Dê um nome (por exemplo, "Karaokê"). Em *Which API/SDKs*, marque **Web API** e **Web Playback SDK**.
3. Em **Redirect URIs**, cole o endereço exato que aparece na tela inicial do app (botão "Copiar"). Por exemplo, `http://127.0.0.1:8888/` ou `https://seu-usuario.github.io/karaoke/`. Ele precisa ser idêntico, inclusive a barra final.
4. Salve e copie o **Client ID**.
5. (Opcional) Em **User Management**, adicione o e-mail de até 5 pessoas que também vão usar o app. Essa lista é o limite do modo de desenvolvimento.

### 3. Conecte

Abra o app, cole o Client ID e clique em **Conectar ao Spotify**. O login usa o fluxo PKCE, ou seja, nenhuma senha ou segredo fica no código. O token fica salvo só no seu navegador.

## Como a parte "karaokê" funciona (e o que não dá para fazer)

- **Remover a voz da gravação original não é possível.** O áudio do Spotify é protegido (DRM) e nenhum app de terceiros tem acesso ao som para processá-lo. Por isso, o app oferece duas saídas: cantar por cima da original (com a letra guiando) ou trocar para uma **versão karaokê/instrumental** que já exista no catálogo, o que existe para muitas músicas populares.
- **As letras vêm do LRCLIB** (lrclib.net), um banco aberto e colaborativo de letras sincronizadas. A API do Spotify não fornece letras. Algumas músicas, principalmente as menos conhecidas, podem não ter letra sincronizada. Nesses casos, o app mostra a letra simples com rolagem automática ou deixa você colar uma em formato LRC.
- **Versões karaokê costumam ter outra introdução**, então a letra pode chegar adiantada ou atrasada. Use "Marcar 1ª frase" ou os botões −/+. O ajuste fica salvo.

## Uso pessoal

- A [política de desenvolvedor do Spotify](https://developer.spotify.com/policy) proíbe sincronizar gravações com conteúdo visual, e as letras do LRCLIB não são licenciadas para uso comercial. Por isso, este projeto serve **para uso pessoal** (você e até 5 convidados, no modo de desenvolvimento). Para um produto público ou comercial, seria preciso licenciar letras e áudio de karaokê de um fornecedor próprio, sem usar o Spotify como fonte de som.
- Limites atuais do modo de desenvolvimento: até 5 usuários por app, busca com no máximo 10 resultados por página (o app pagina com "carregar mais") e cota de requisições compartilhada por conta.

## Problemas comuns

| Mensagem / sintoma | O que fazer |
|---|---|
| `INVALID_CLIENT: Invalid redirect URI` | O endereço cadastrado no Dashboard não é idêntico ao da tela inicial (confira `http` x `https`, a porta e a barra final). |
| "Nenhum aparelho ativo" | Abra o app do Spotify no celular ou no PC, dê play em qualquer música por 1 segundo e toque em "↻ Atualizar aparelhos". |
| 403 ao buscar ou tocar | A conta que fez login precisa estar em *User Management* no Dashboard, e o dono do app precisa ter Premium ativo. |
| No celular não sai som pelo navegador | Isso é esperado. Escolha o seu celular (app do Spotify) como aparelho, e a letra continua aqui. |
| Letra fora do tempo | Use "Marcar 1ª frase" ou −/+ (0,25 s por toque). |
