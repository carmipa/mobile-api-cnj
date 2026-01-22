# 🚀 Guia de Deploy

Este documento descreve como fazer deploy da aplicação Mobile API CNJ para produção.

## 📋 Pré-requisitos

- [ ] Node.js 18+ instalado
- [ ] Expo CLI (`npm install -g expo-cli`)
- [ ] EAS CLI (`npm install -g eas-cli`)
- [ ] Conta Expo criada
- [ ] Certificados iOS e Android configurados
- [ ] Secrets do GitHub configurados

## 🔐 Configuração de Secrets

No repositório GitHub, configure os seguintes secrets:

```
EXPO_TOKEN              # Token de autenticação Expo
APPLE_TEAM_ID          # Apple Team ID
APPLE_DEVELOPER_ID     # Apple Developer ID  
ANDROID_KEYSTORE       # Base64 do arquivo .jks
ANDROID_KEYSTORE_PASS  # Senha do keystore
ANDROID_KEY_ALIAS      # Alias da chave
ANDROID_KEY_PASS       # Senha da chave
```

## 🚀 Deploy Automático

### Via GitHub Actions

O deploy é acionado automaticamente ao fazer push para `main` ou ao criar uma tag:

```bash
# Criar release
git tag v1.0.0
git push origin v1.0.0
```

Ou manualmente:

```bash
# Ir para Actions > Build & Release > Run workflow
# Selecionar ambiente e plataforma
```

## 🔨 Build Local

### Android

```bash
# Build de desenvolvimento
eas build --platform android --profile preview

# Build de produção
eas build --platform android --profile production

# Criar APK local
npm run android

# Criar AAB (Google Play)
eas build --platform android
```

### iOS

```bash
# Build de desenvolvimento
eas build --platform ios --profile preview

# Build de produção
eas build --platform ios --profile production
```

### Web

```bash
# Build para web
expo export --platform web

# Servir localmente
npm run web
```

## 📱 Distribuição

### Google Play Store

1. Fazer login no Google Play Console
2. Criar novo app ou usar existente
3. Upload do AAB build
4. Configurar store listing
5. Submeter para review

```bash
eas submit --platform android
```

### Apple App Store

1. Fazer login no App Store Connect
2. Criar novo app ou usar existente
3. Upload do build via Transporter
4. Configurar app listing
5. Submeter para review

```bash
eas submit --platform ios
```

### Web (Vercel/Netlify)

```bash
# Vercel
vercel --prod

# Netlify
netlify deploy --prod --dir=web-build
```

## ✅ Checklist de Deploy

### Antes de Fazer Deploy

- [ ] Todos os testes passando
- [ ] CI/CD pipeline com sucesso
- [ ] Código review aprovado
- [ ] Versão atualizada em package.json
- [ ] CHANGELOG atualizado
- [ ] Documentação atualizada
- [ ] Secrets configurados
- [ ] Build local testado

### Durante o Deploy

- [ ] Monitorar GitHub Actions
- [ ] Verificar logs de build
- [ ] Confirmar upload bem-sucedido
- [ ] Testar versão em staging

### Após o Deploy

- [ ] Monitorar aplicação
- [ ] Verificar erros em produção
- [ ] Responder a feedback do usuário
- [ ] Estar preparado para rollback

## 🔄 Rollback

Se houver problemas em produção:

```bash
# Reverter para versão anterior
git revert <commit-hash>
git push origin main

# Ou criar hotfix
git checkout -b hotfix/issue-name
# ... fazer correções ...
git commit -m "fix: descrição do problema"
git push origin hotfix/issue-name
# Criar PR para main
```

## 📊 Monitoramento

Após deploy, monitorar:

- 📊 Crashes e erros
- ⚡ Performance
- 👥 Engagement dos usuários
- 🐛 Bugs reportados
- 📈 Métricas de adoção

## 🆘 Troubleshooting

### Build falhou
1. Verificar logs
2. Validar dependências
3. Limpar cache: `npm cache clean --force`
4. Tentar novamente

### EAS token expirado
```bash
eas login
eas whoami
```

### Certificados vencidos
- Renovar certificados Apple/Android
- Atualizar em GitHub Secrets
- Reconstruir

## 📞 Suporte

- 🐛 Bugs: [Issues](https://github.com/carmipa/mobile-api-cnj/issues)
- 📧 Email: deploy@mobile-api-cnj.dev
