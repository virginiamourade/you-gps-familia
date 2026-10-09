# You GPS Família — protótipo Android (web)

## Configuração necessária para dois aparelhos

1. Crie um projeto em https://console.firebase.google.com/.
2. Adicione um aplicativo **Web** e copie os valores de configuração para `firebase-config.js`.
3. Em **Authentication > Sign-in method**, habilite **Anonymous**.
4. Em **Firestore Database**, crie um banco de dados e, em **Rules**, cole o conteúdo de `firestore.rules` e publique.
5. Envie `index.html` e `firebase-config.js` ao repositório GitHub e publique na Vercel. O arquivo `firestore.rules` serve para configurar o console, não é usado diretamente pelo navegador.
6. No Android da pessoa que compartilhará: abra a URL HTTPS, toque em **Compartilhar minha localização** e em **Iniciar compartilhamento**, autorize o GPS e envie o código temporário de 12 caracteres à pessoa escolhida.
7. No segundo aparelho: abra a mesma URL, selecione **Acompanhar com convite**, insira o código e toque em **Acompanhar**.
8. Para encerrar, use **Parar compartilhamento** no aparelho que transmite. O convite expira após uma hora.

## Limites e cuidados

- O site **não localiza pessoas por número de telefone**.
- O navegador Android pode pausar localização quando a tela é bloqueada, quando o site vai para segundo plano ou por economia de bateria.
- O mapa exige internet e o acesso à localização exige HTTPS.
- O rastro no mapa é apenas da sessão atual do navegador que acompanha; não há banco de histórico.
- A sessão contém localização sensível. O código de 12 caracteres é um segredo de acesso: compartilhe apenas com quem você deseja autorizar. O protótipo não oferece autenticação forte, revogação individual de espectadores nem garantia de funcionamento em emergência. Não o utilize como solução de segurança pessoal ou de monitoramento institucional.
- Para uso real mais robusto, implementar autenticação por contas, regras de acesso por participante, exclusão automática de sessões e app Android nativo com aviso permanente de compartilhamento.
- Se o navegador fechar inesperadamente, a localização deixa de atualizar, mas o documento pode continuar marcado como ativo até expirar; o painel mostra o horário da última atualização.
