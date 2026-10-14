# Cuidados

Aplicativo pessoal para Android, feito com Expo SDK 57 e React Native. Os artigos ficam no app e as datas de acompanhamento são guardadas somente no aparelho com AsyncStorage. Não há servidor nem conta.

## Rodar

```bash
npm install
npm start
```

Para gerar o bundle Android e verificar o código:

```bash
npm run catalog
npx tsc --noEmit
npm run lint
npx expo export --platform android
```

## Conteúdo

Os ambientes estão em `content/sections.json`. Cada cuidado é um JSON separado em `content/`. O campo `section` do artigo aponta para o `id` do ambiente. Título, texto, fontes, intervalo sugerido e frases dos lembretes vêm desses arquivos. Ao adicionar ou editar um JSON, execute `npm run catalog` (também roda automaticamente antes de `npm start`, `npm run android`, `npm run web` e `npm run lint`).

As datas, os intervalos personalizados e o horário dos lembretes ficam separados do conteúdo editorial. O prazo é presumido após passar o dia previsto; a interface distingue presunção de ação confirmada. Registrar a data real reinicia o ciclo a partir dela.

## Testar o aviso agrupado

No Android, abra **Ajustes → Teste das notificações → Preparar teste**. O app guarda suas datas e preferências, configura os quatro cuidados para o dia seguinte e agenda um aviso agrupado para 12h da véspera. Se 12h já passou no horário local do aparelho, agenda para alguns minutos à frente. A tela confirma se encontrou exatamente um aviso agrupado na fila do Android. Depois de conferir a entrega, toque em **Restaurar minhas datas e horário**. Deixe as notificações permitidas nas configurações do aparelho.

## APK pessoal

O perfil `preview` em `eas.json` gera um APK para instalação direta. Depois de entrar na sua conta Expo:

```bash
npx eas-cli@latest login
npx eas-cli@latest build --platform android --profile preview
```

O identificador Android é `com.fagne.cuidados`. Para futuras atualizações, preserve esse identificador e as credenciais de assinatura geridas pelo EAS, e aumente `android.versionCode` em `app.json`. Teste as notificações no aparelho, incluindo a permissão do Android e o horário de 20h, antes de confiar nos lembretes.
# cuidados
