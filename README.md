# Guia Simplificado de Apache FreeMarker

## 🔗 Recursos e Links úteis
- Site oficial: [https://freemarker.apache.org/](https://freemarker.apache.org/)
- Documentação completa: [https://freemarker.apache.org/docs/](https://freemarker.apache.org/docs/)
- Repositório no GitHub: [https://github.com/apache/freemarker](https://github.com/apache/freemarker)
- Tutoriais e exemplos: [https://freemarker.apache.org/docs/dgui.html](https://freemarker.apache.org/docs/dgui.html)

---

## 📂 Sintaxe Básica

### 1. Exibir Variáveis
As variáveis são passadas do código Java para o template.
```ftl
Olá, ${nome}! Você tem ${idade} anos.
```
Se `nome = "João"` e `idade = 30`, a saída será:
```
Olá, João! Você tem 30 anos.
```

Definir um valor padrão caso a variável não exista:
```ftl
${nome!"Usuário Anônimo"}
```

---

### 2. Estruturas de Controle

#### 2.1 Condicionais (`if`, `else if`, `else`)
```ftl
<#if idade >= 18>
    Você é maior de idade.
<#elseif idade >= 13>
    Você é adolescente.
<#else>
    Você é menor de idade.
</#if>
```

#### 2.2 Estruturas de Decisão (`switch-case`)
```ftl
<#switch status>
    <#case "pendente">
        Pedido ainda não processado.
        <#break>
    <#case "enviado">
        Pedido a caminho.
        <#break>
    <#default>
        Status desconhecido.
</#switch>
```

---

### 3. Laços de Repetição

#### 3.1 Loop `list`
```ftl
<#list produtos as produto>
    Produto: ${produto.nome} - Preço: ${produto.preco}
</#list>
```

#### 3.2 Loop com Índice
```ftl
<#list produtos as produto>
    ${produto_index + 1}. ${produto.nome}
</#list>
```

---

### 4. Trabalhando com Listas e Dicionários

#### 4.1 Criando Listas (Arrays)
```ftl
<#assign frutas = ["Maçã", "Banana", "Laranja"]>
Primeira fruta: ${frutas[0]}
```

#### 4.2 Criando Dicionários (Mapas)
```ftl
<#assign pessoa = {"nome": "Lucas", "idade": 30}>
Nome: ${pessoa.nome}, Idade: ${pessoa.idade}
```

#### 4.3 Iterando sobre um Dicionário
```ftl
<#list pessoa?keys as chave>
    ${chave}: ${pessoa[chave]}
</#list>
```

---

### 5. Criando Funções Personalizadas (Macros)

#### 5.1 Definindo e Chamando uma Macro
```ftl
<#macro saudacao nome>
    Olá, ${nome}! Bem-vindo ao sistema.
</#macro>

<@saudacao nome="João"/>
```

#### 5.2 Macro com Vários Parâmetros
```ftl
<#macro info usuario idade>
    Nome: ${usuario}, Idade: ${idade}
</#macro>

<@info usuario="Carlos" idade=25/>
```

---

### 6. Trabalhando com Templates

#### 6.1 Incluir Arquivos (`include`)
```ftl
<#include "header.ftl">
Bem-vindo ao site!
<#include "footer.ftl">
```

#### 6.2 Importar Macros (`import`)
```ftl
<#import "macros.ftl" as m>
<@m.saudacao nome="Maria"/>
```

---

### 7. Funções Úteis

#### 7.1 Converter Texto para Maiúscula/Minúscula
```ftl
${"texto"?upper_case} <!-- TEXTO -->
${"TEXTO"?lower_case} <!-- texto -->
```

#### 7.2 Formatar Números
```ftl
<#assign preco = 1999.99>
Preço formatado: ${preco?string(",0.00")}
```

#### 7.3 Obter Data Atual
```ftl
Hoje é: ${.now?string("dd/MM/yyyy")}
```

---

## 🔮 Conclusão
Este guia apresenta os principais recursos do **Apache FreeMarker**, incluindo **exibição de variáveis, controle de fluxo, listas, dicionários e macros**. Com essas informações, você pode criar templates dinâmicos de forma eficiente.

*Nickz :)*

