#NCOR — Laudos de Doppler de Carótidas e Vertebrais

Gerador de laudos de **ultrassonografia com Doppler de carótidas e vertebrais**, em arquivo HTML único, sem servidor e sem dependências de instalação. Roda inteiramente no navegador, com identidade visual da **Encor — Núcleo de Endocrinologia e Cardiologia**.

> **Uso clínico restrito.** Ferramenta de apoio à redação de laudos por médico habilitado. Não substitui avaliação clínica, julgamento profissional nem a interpretação direta das imagens. A responsabilidade pelo conteúdo final do laudo é integralmente do médico assinante.

---

## Recursos

- **Motor de conclusão automática** para ACC, bifurcação carotídea, ACI, ACE e artéria vertebral, com texto editável (a edição manual sobrepõe o automático).
- **Classificação de estenose de ACI pelos critérios IAC (consenso SRU modificado):** normal/<50%, 50–69% e ≥70% (suboclusiva), a partir de VPS, EDV e razão ACI/ACC.
- **Detecção de roubo de subclávia** pela artéria vertebral (fluxo alternante/parcial e retrógrado/completo).
- **Campos estruturados de placa** (em vez de texto livre).
- **Ditado por voz** via Web Speech API (quando suportado pelo navegador).
- **Geração de PDF** do laudo formatado em A4, com auto-ajuste de página.
- **Salvamento direto em pasta de destino** escolhida pelo usuário (File System Access API), com fallback automático para Downloads.
- **Banco de pacientes local** para salvar e recarregar laudos.
- **Impressão** com timbrado e assinatura.
- **Autotestes** internos do motor de laudo.

---

## Requisitos

- **Navegador:** Chrome ou Edge atualizados (recomendado). O salvamento direto em pasta e o ditado por voz dependem de APIs disponíveis principalmente nesses navegadores.
- **Contexto seguro:** a escolha de pasta de destino (`showDirectoryPicker`) exige **HTTPS** ou **localhost**. Em `file://` ou HTTP simples, o PDF é sempre baixado na pasta Downloads.

---

## Como usar

1. Abra o arquivo HTML no navegador (ou a URL do GitHub Pages).
2. Preencha os dados do paciente e os achados por segmento/lado.
3. Revise a conclusão gerada; edite o texto se necessário.
4. (Opcional) Clique em **📁 Pasta PDF** para definir a pasta de destino dos laudos.
5. Clique em **PDF** para gerar o laudo.

### Salvamento em pasta

Após escolher a pasta, os PDFs são gravados diretamente nela. Ao **recarregar a página**, o navegador pode pedir novamente a permissão de acesso à pasta — basta autorizar quando solicitado. Se a permissão não for concedida, o PDF é baixado na pasta Downloads e o app avisa explicitamente.

### Atalhos de teclado

| Atalho | Ação |
|---|---|
| `Ctrl + N` | Novo laudo |
| `Ctrl + S` | Salvar paciente |
| `Ctrl + L` | Abrir banco de pacientes |
| `Ctrl + P` | Imprimir |
| `Ctrl + Shift + S` | Gerar PDF |
| `Ctrl + Shift + C` | Copiar conclusão |

### Autotestes

Abra o app com `#test` no final da URL (ou chame `runSelfTests()` no console) para rodar a bateria de testes do motor de classificação e conclusão.

---

## Publicação no GitHub Pages

1. Coloque o arquivo principal na raiz do repositório com o nome **`index.html`** (o GitHub Pages só serve a página inicial automaticamente com esse nome e extensão).
2. Em **Settings → Pages**, selecione a branch (`main`) e a pasta `/ (root)`.
3. Aguarde a publicação; o app ficará disponível na URL informada pelo GitHub Pages.

> Como o GitHub Pages serve por HTTPS, o salvamento direto em pasta funciona normalmente nesse ambiente.

---

## Privacidade e dados

- **100% local.** Nenhum dado de paciente é enviado a servidores; todo o processamento ocorre no navegador.
- O **banco de pacientes** é armazenado em `localStorage` e a **referência da pasta de destino** em IndexedDB, ambos restritos ao navegador/dispositivo em uso.
- Limpar os dados do site no navegador apaga o banco local de pacientes.

---

## Estrutura

Aplicativo de **arquivo único** (`index.html`): HTML, CSS e JavaScript embutidos, incluindo timbrado e assinatura. Dependências carregadas via CDN: `html2canvas` e `jsPDF`. O empacotamento como PWA (manifest + service worker + bibliotecas locais) é distribuído como bundle separado.

---

## Referências clínicas

- Critérios **IAC (Intersocietal Accreditation Commission)** — modificação do consenso **SRU (Society of Radiologists in Ultrasound)** para classificação de estenose carotídea.
- ESVS e SBACV/CBR como referências complementares.

---

## Autoria

**Dr. Genius Costa** — Cardiologia e Ecocardiografia
CRM-BA 23913 · RQE 15055 (Clínica Médica) · RQE 15021 (Cardiologia) · RQE 16630 (Ecocardiografia)
**Encor — Núcleo de Endocrinologia e Cardiologia** · Barreiras, BA

---

## Versão

`v.carotida-11.10.3`
