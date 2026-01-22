# 🔒 Política de Segurança

## Reportando Vulnerabilidades

Se você descobrir uma vulnerabilidade de segurança, **não** crie uma issue pública. Em vez disso, por favor, envie um email para:

📧 **security@mobile-api-cnj.dev**

Inclua:
- Descrição da vulnerabilidade
- Passos para reproduzir
- Impacto potencial
- Sugestões de correção (se houver)

Nós agradecemos sua paciência e vamos trabalhar rapidamente para:
1. Confirmar o problema
2. Desenvolver uma correção
3. Lançar uma atualização de segurança

## Práticas de Segurança

### Dependências

- Monitoramos regularmente vulnerabilidades com `npm audit`
- Atualizamos dependências críticas imediatamente
- Mantemos um histórico de vulnerabilidades encontradas

### Dados Sensíveis

- **Nunca** commita secrets, chaves API ou tokens
- Use `.gitignore` para excluir arquivos sensíveis
- Revise commits antes de fazer push
- Rotacione chaves/tokens comprometidos imediatamente

### Certificados

- Certificados Android (`.jks`) devem ser mantidos privados
- Use GitHub Secrets para armazenar informações sensíveis
- Não compartilhe credenciais de desenvolvimento

## Versões Suportadas

| Versão | Suportada | Notas |
|--------|-----------|-------|
| 1.x    | ✅ Yes    | Versão atual |
| < 1.0  | ❌ No     | Versão obsoleta |

## Atualizações de Segurança

- Patches de segurança são lançados o mais rápido possível
- Alteramos números patch para fixes de segurança
- Anunciamos atualizações de segurança no README e releases

## Contato

- 🐛 Bugs: [GitHub Issues](https://github.com/carmipa/mobile-api-cnj/issues)
- 🔒 Segurança: security@mobile-api-cnj.dev
- 💬 Discussões: [GitHub Discussions](https://github.com/carmipa/mobile-api-cnj/discussions)
