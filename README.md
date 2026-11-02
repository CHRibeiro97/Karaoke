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

## Animações no palco

As animações seguem a ideia dos jogos de ritmo, com visual próprio do app:

- **Pista de notas**: cada frase da letra vem descendo como uma nota colorida, com uma "cauda" do tamanho da frase. Quando a nota chega na barra dourada, solta faíscas.
- **Micão**: mascote em forma de microfone que dança no ritmo da música. Ele pula e gira quando o cantor tira "Perfeito!", agita os braços no "Ótimo!" e fica cabisbaixo no "Ops…".
- **Plateia**: balança no ritmo, levanta os braços nos acertos e acende as lanternas do celular a partir de 8 acertos seguidos.
- **Combo em chamas**: a partir de 5 acertos seguidos, a borda da tela pega fogo. Também há chuva de confete no resultado e no aplauso.
- Em 🏆 Festa → **Animações**, dá para escolher **Completas**, **Leves** (para celular ou TV mais fracos) ou **Desligadas**.

## Letras: busca manual e biblioteca própria

- **Buscar letra**: no palco, toque em **Letra…**. O app já busca com o nome da música, e você pode reescrever do jeito que quiser e escolher o resultado certo. Cada resultado mostra a duração e se a letra é sincronizada.
- **📚 Minha biblioteca** (em ⚙ ou em 🏆 Festa): guarda as letras escolhidas, coladas e sincronizadas no toque, além dos ajustes de sincronia. Dá para **exportar** um arquivo, **compartilhar** pelo WhatsApp e outros apps, ou **importar** no outro aparelho. Importar só soma, nunca apaga.

## Dueto com dois celulares

Um segundo celular pode virar o **2º microfone**. Cada celular calcula a nota de quem está cantando nele.

1. **Sala da festa**: se tiver TV conectada, o código da TV já é a sala. Sem TV, vá em **📺 Conectar à TV → Criar sala para dueto** no celular principal.
2. No 2º celular, abra o endereço do app, toque em **📱 Entrar como 2º microfone**, digite o seu nome e o código da sala. Ele não precisa de conta no Spotify.
3. No celular principal, aparece um pedido de liberação. Ao aceitar, o login é passado para o 2º celular (o Spotify pode piscar a tela por um segundo).
4. No 2º celular, toque em **🎤 Ativar microfone**. Ele fica esperando.
5. Ao escolher uma música, a janela "Quem vai cantar?" passa a ter **🎤🎤 Dueto**: escolha quem canta em cada celular e como dividir:
   - **Revezando as partes**: a letra é dividida em blocos (pelas pausas da música). A pessoa A canta um bloco, a B canta o seguinte, e o último bloco é dos dois juntos.
   - **Os dois cantam tudo**.
6. Na tela, cada frase vem marcada com a cor de quem canta (rosa = celular principal, azul = 2º celular, dourado = juntos), e um aviso mostra "Vez de…".
7. No fim, sai a **nota de cada um** e a **nota da dupla**: a média das duas, mais um bônus de até 5 pontos por *sintonia* (quanto mais parecidas as notas, maior o bônus). O aplauso vale para a dupla. A TV mostra tudo isso.

As notas entram no ranking de cada participante, marcadas como dueto.

## Modo TV (Samsung e outras Smart TVs)

A TV vira a tela do show, e o celular vira o microfone e o controle:

1. Na TV, abra o navegador **Internet** e acesse o endereço do app. A TV entra sozinha no **modo TV** e mostra um código de 6 letras. Vale salvar o endereço nos favoritos.
2. No celular, toque em **🏆 Festa → 📺 Conectar à TV** e digite o código. O celular faz o login do Spotify na TV, então não precisa digitar senha com o controle remoto.
3. Para o som sair na TV, abra o **app do Spotify da TV** e, no palco do celular, escolha a TV como aparelho.
4. A partir daí, a TV mostra a letra do que estiver tocando, com as animações, quem está cantando, a nota ao vivo e o resultado. O aplauso é medido pelo celular.

Pelo controle remoto: **OK** toca e pausa, **◀ ▶** voltam e avançam 5 s, e **▲ ▼** ajustam a sincronia da letra.

Limitações:

- O navegador da TV não acessa microfone e não toca o Spotify sozinho. Por isso, o som vem do app do Spotify da TV e o microfone é o do celular.
- O modo karaokê da Samsung (microfone pelo celular via SmartThings) é exclusivo do app Stingray Karaoke, e este app não consegue usar esse recurso. Por isso, o app não amplifica a sua voz nas caixas da TV.
- Se a música parar quando você sai do app do Spotify da TV para o navegador, toque a música pelo celular numa caixa de som Bluetooth, ou espelhe o som do celular na TV.
- A TV e o celular conversam pelo serviço público gratuito **ntfy.sh**. As mensagens são criptografadas com o código da TV e só levam o login, a letra, as notas e os nomes. O serviço limita a quantidade de mensagens, por isso a nota ao vivo na TV atualiza a cada ~12 s.

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
| Letra não encontrada | No palco, toque em **Letra…** e busque com outro nome (por exemplo, sem "ao vivo" ou "feat."), ou cole a letra. |
| A TV não sai da tela do código | Confira se digitou o código certo e se o celular está conectado ao Spotify. Se a TV foi reiniciada, o código continua o mesmo. |
| A TV mostra a letra, mas sem som | Abra o app do Spotify da TV e escolha a TV como aparelho no palco do celular. |
| O computador abriu no modo TV sem querer | Na tela da TV, toque em "Sair do modo TV". |
| O pedido do 2º microfone não aparece | No 2º celular, toque em "Pedir para entrar de novo". O celular principal precisa estar com o app aberto e conectado à sala. |
| O 2º celular não pontua | Toque em "🎤 Ativar microfone" e libere o microfone no navegador. A tela dele precisa ficar acesa. |
| A opção de dueto não aparece | O 2º celular precisa ter sido liberado, e precisam existir pelo menos 2 participantes no 🏆 Festa. |
