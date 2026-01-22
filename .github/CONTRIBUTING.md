# 🤝 Guia de Contribuição

Obrigado por estar interessado em contribuir com o **Mobile API CNJ**! 💙

## 📋 Índice

- [Código de Conduta](#código-de-conduta)
- [Como Começar](#como-começar)
- [Processo de Desenvolvimento](#processo-de-desenvolvimento)
- [Padrões de Código](#padrões-de-código)
- [Enviando Mudanças](#enviando-mudanças)
- [Pull Request Process](#pull-request-process)
- [Reportando Bugs](#reportando-bugs)
- [Sugerindo Enhancements](#sugerindo-enhancements)
- [Contato](#contato)

## 📜 Código de Conduta

Este projeto e todos participantes estão sujeitos ao [Código de Conduta](./CODE_OF_CONDUCT.md). Ao participar, você concorda em manter um ambiente respeitoso e inclusivo.

### Nossa Promessa

No interesse de promover um ambiente aberto e acolhedor, nós, como colaboradores e mantenedores, nos comprometemos a fazer com que participar em nosso projeto e comunidade seja uma experiência livre de assédio para todos, independentemente de idade, tamanho do corpo, deficiência, etnia, identidade e expressão de gênero, nível de experiência, nacionalidade, aparência pessoal, raça, religião ou identidade e orientação sexual.

## 🚀 Como Começar

### Pré-requisitos

- Node.js 18+
- npm ou yarn
- Expo CLI
- Git

### Setup Inicial

```bash
# 1. Fork o repositório
# 2. Clone o seu fork
git clone https://github.com/seu-usuario/mobile-api-cnj.git
cd mobile-api-cnj

# 3. Adicione upstream
git remote add upstream https://github.com/carmipa/mobile-api-cnj.git

# 4. Instale dependências
npm install

# 5. Crie uma branch
git checkout -b feature/sua-feature
```

## 🔄 Processo de Desenvolvimento

### Branch Naming Convention

```
feature/nome-da-feature          # Nova feature
fix/descricao-do-bug             # Correção de bug
docs/o-que-foi-documentado       # Documentação
refactor/o-que-foi-refatorado    # Refatoração
test/o-que-foi-testado           # Testes
chore/o-que-foi-atualizado       # Manutenção
```

### Commit Message Convention

```
<tipo>(<escopo>): <assunto>

<corpo>

<footer>
```

#### Tipos
- **feat**: Nova feature
- **fix**: Correção de bug
- **docs**: Mudanças em documentação
- **style**: Formatação, sem mudanças lógicas
- **refactor**: Refatoração de código
- **test**: Adição ou atualização de testes
- **chore**: Atualizações de build, deps, etc
- **perf**: Melhoria de performance
- **ci**: Mudanças em CI/CD

#### Exemplos

```
feat(api): adicionar busca avançada de processos

Implementa novo endpoint de busca com suporte a filtros avançados
e paginação automática.

Fixes #123
```

```
fix(ui): corrigir alinhamento do botão na tela de favoritos

Remove padding incorreto que causava desalinhamento em dispositivos pequenos.
```

## 📝 Padrões de Código

### JavaScript/React Native

```javascript
// ✅ BOM
const fetchProcessData = async (processNumber) => {
  try {
    // Busca dados do processo
    const response = await axios.get(`/api/processes/${processNumber}`);
    return response.data;
  } catch (error) {
    console.error('Erro ao buscar processo:', error);
    throw error;
  }
};

// ❌ EVITAR
const f = async (n) => {
  // Código obscuro
  return await api.get(`/p/${n}`);
};
```

### Naming Conventions

```javascript
// Componentes - PascalCase
const HomeScreen = () => {};
const UserCard = () => {};

// Funções/Variáveis - camelCase
const getUserInfo = () => {};
const isProcessValid = true;
const CONSTANTS_VALUE = 100; // Constantes - UPPER_SNAKE_CASE

// Arquivos
// Componentes: HomeScreen.js
// Utilitários: pdfService.js
// Contextos: ThemeContext.js
```

### Padrões de Componentes

```javascript
import React, { useState, useCallback } from 'react';
import { View, Text, StyleSheet } from 'react-native';

/**
 * Descrição clara do componente
 * 
 * @param {Object} props - Props do componente
 * @param {string} props.title - Título do componente
 * @param {function} props.onPress - Callback ao pressionar
 * @returns {React.Component}
 */
const MyComponent = ({ title, onPress }) => {
  const [state, setState] = useState(null);
  
  const handlePress = useCallback(() => {
    onPress?.();
  }, [onPress]);

  return (
    <View style={styles.container}>
      <Text style={styles.title}>{title}</Text>
    </View>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    padding: 16,
  },
  title: {
    fontSize: 18,
    fontWeight: 'bold',
  },
});

export default MyComponent;
```

### Comentários

```javascript
// ✅ BOM - Explica o "por quê"
// Usamos useMemo aqui para evitar re-renders desnecessários
// quando os dados não mudaram
const memoizedValue = useMemo(() => computeValue(a, b), [a, b]);

// ❌ EVITAR - Apenas descreve o que o código faz
// Cria um valor memorizado
const value = useMemo(() => computeValue(a, b), [a, b]);

// ❌ MUITO EVITAR - Comentários óbvios
// Incrementa i
i++;
```

### Indentação

- Use **2 espaços** (não tabs)
- Máximo 80 caracteres por linha quando possível

## 📤 Enviando Mudanças

### 1. Sincronize sua branch com main

```bash
git fetch upstream
git rebase upstream/main
```

### 2. Faça commits pequenos e atômicos

```bash
# BOM - Um commit por mudança lógica
git commit -m "feat(api): adicionar filtro por tribunal"
git commit -m "test(api): adicionar testes para filtro"

# EVITAR - Múltiplas mudanças em um commit
git commit -m "fixes vários bugs e adiciona features"
```

### 3. Push para seu fork

```bash
git push origin feature/sua-feature
```

### 4. Crie um Pull Request

## 🔀 Pull Request Process

### Checklist para PR

- [ ] Descrição clara do que foi mudado
- [ ] Link para issue relacionada (se houver)
- [ ] Testes adicionados/atualizados
- [ ] Documentação atualizada
- [ ] Nenhum breaking change sem discussão
- [ ] CI/CD passing

### Review Process

1. **Análise Automática**
   - CI/CD precisa passar
   - Coverage checks
   - Linting

2. **Revisão Manual**
   - Maintainers fazem code review
   - Feedback pode ser solicitado
   - Aprovação necessária para merge

3. **Merge**
   - PRs são squashed e merged
   - Branch é deletada automaticamente

## 🐛 Reportando Bugs

### Antes de Reportar

- [ ] Verifique issues existentes
- [ ] Atualize para a versão mais recente
- [ ] Tente reproduzir o bug
- [ ] Colete informações do ambiente

### Como Reportar

Use o [template de bug](ISSUE_TEMPLATE/bug_report.md)

```markdown
## 📋 Descrição do Bug
[Descrição clara]

## 🔄 Passos para Reproduzir
1. ...
2. ...
3. ...

## ✅ Comportamento Esperado
[Descrição]

## 📱 Ambiente
- Plataforma: Android/iOS
- Versão do Expo: X.X.X
```

## 💡 Sugerindo Enhancements

Use o [template de feature](ISSUE_TEMPLATE/feature_request.md)

```markdown
## 📝 Descrição
[Descrição da feature]

## 💡 Motivação
[Por que isso seria útil?]

## 🎯 Comportamento Esperado
[Como deveria funcionar?]
```

## 🆘 Dúvidas?

- 💬 [Discussões GitHub](https://github.com/carmipa/mobile-api-cnj/discussions)
- 🐛 [Issues](https://github.com/carmipa/mobile-api-cnj/issues)
- 📧 Email: support@mobile-api-cnj.dev

## 📚 Recursos Úteis

- [React Native Docs](https://reactnative.dev/)
- [Expo Docs](https://docs.expo.dev/)
- [Git Workflow](https://guides.github.com/introduction/flow/)
- [Semantic Versioning](https://semver.org/)

---

**Obrigado por contribuir! ❤️**
