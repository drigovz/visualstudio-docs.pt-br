---
title: Compilador de cores VSIX | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f414a56bb05a23b6efef19aa7c99292b8a40038a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703897"
---
# <a name="vsix-color-compiler"></a>Compilador de cores do VSIX
A ferramenta Visual Studio Extension Color Compiler é um aplicativo de console que pega um arquivo .xml representando cores para os temas existentes do Visual Studio e o encobre para um arquivo .pkgdef para que essas cores possam ser usadas no Visual Studio. Como é fácil comparar diferenças entre arquivos .xml, esta ferramenta é útil para gerenciar cores personalizadas no controle de origem. Ele também pode ser ligado a ambientes de construção para que a saída da compilação seja um arquivo .pkgdef válido.

 **Esquema XML temático**

 Um arquivo completo .xml se parece com isso:

```xml
<Themes>
      <!—one or Theme elements -->
      <Theme>
        <!-- one or more Category elements -->
        <Category>
          <!-- one or more Color elements -->
          <Color>
            <!-- zero or one Background element -->
            <Background />
            <!-- zero or one Foreground element -->
            <Foreground />
          </Color>
        </Category>
      </Theme>
</Themes>
```

 **Tema**

 O \<tema> elemento define um tema inteiro. Um tema deve conter \<pelo menos um elemento de> categoria. Os elementos temáticos são definidos assim:

```xml
<Theme Name="name" GUID="guid">
      <!-- one or more Category elements -->
</Theme>
```

|||
|-|-|
|**Atributo**|**Definição**|
|Nome|[Necessário] O nome do tema|
|GUID|[Necessário] Guid do tema (deve corresponder à formatação GUID)|

 Ao criar cores personalizadas para o Visual Studio, essas cores precisam ser definidas para os seguintes temas. Se não existirem cores para um tema específico, o Visual Studio tentará carregar as cores ausentes do tema Luz.

|||
|-|-|
|**Nome do tema**|**TEMA GUID**|
|Leve|{de3dbbcd-f642-433c-8353-8f1df4370aba}|
|Escuro|{1ded0138-47ce-435e-84ef-9ec1f439b749}|
|Azul|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|
|Alto Contraste|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|

 **Categoria**

 O \<elemento Categoria> define uma coleção de cores em um tema. Os nomes das categorias fornecem agrupamentos lógicos e devem ser definidos da forma mais estreita possível. Uma categoria deve conter \<pelo menos um elemento de> de Cor. Os elementos da categoria são definidos assim:

```xml
<Category Name="name" GUID="guid">
      <!-- one or more Color elements -->
 </Category>
```

|||
|-|-|
|**Atributo**|**Definição**|
|Nome|[Necessário] O nome da categoria|
|GUID|[Necessário] Guid da categoria (deve corresponder à formatação GUID)|

 **Cor**

 O \<elemento Color> define uma cor para um componente ou estado de UI. O esquema de nomeação preferido para uma cor é [tipo de ui] [Estado]. Não use a palavra "cor", pois é redundante. Uma cor deve indicar claramente o tipo de elemento e as situações, ou "estado", para o qual a cor será aplicada. Uma cor não deve estar vazia e deve \<conter um \<ou ambos de um elemento de> de fundo e de> em primeiro plano. Os elementos de cor são definidos assim:

```xml
<Color Name="name">
        <Background /> <!-- zero or one Background element -->
        <Foreground /> <!-- zero or one Foreground element -->
 </Color>
```

|||
|-|-|
|**Atributo**|**Definição**|
|Nome|[Necessário] O nome da cor|

 **Fundo e/ou Primeiro Plano**

 Os \<elementos \<de> de fundo e de> de primeira definição definem o valor e o tipo de uma cor para o fundo ou primeiro plano de um elemento de IA. Esses elementos não têm filhos.

```xml
<Background Type="type" Source="int" />
<Foreground Type="type" Source="int" />
```

|||
|-|-|
|**Atributo**|**Definição**|
|Type|[Necessário] O tipo de cor. Pode ser um dos seguintes:<br /><br /> *CT_INVALID:* A cor é inválida ou não definida.<br /><br /> *CT_RAW:* Um valor ARGB bruto.<br /><br /> *CT_COLORINDEX:* NÃO USE.<br /><br /> *CT_SYSCOLOR:* Uma cor do sistema Windows do SysColor.<br /><br /> *CT_VSCOLOR:* Uma cor do Visual Studio de __VSSYSCOLOREX.<br /><br /> *CT_AUTOMATIC:* A cor automática.<br /><br /> *CT_TRACK_FOREGROUND:* NÃO USE.<br /><br /> *CT_TRACK_BACKGROUND:* NÃO USE.|
|Fonte|[Necessário] O valor da cor representada no hexadecimal|

 Todos os valores suportados pela enumeração __VSCOLORTYPE são suportados pelo esquema no atributo Tipo. No entanto, recomendamos que você use apenas CT_RAW e CT_SYSCOLOR.

 **Todos juntos**

 Este é um exemplo simples de um arquivo .xml com um tema válido:

```xml
<Themes>
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">
    <Category Name="MyCategory" GUID="{0A96238B-70CE-4479-9170-EECEAA3FCD58}">
      <Color Name="MyActiveBorder">
        <Background Type="CT_RAW" Source="FFCCCEDB" />
      </Color>
    </Category>
  </Theme>
</Themes>
```

## <a name="how-to-use-the-tool"></a>Como usar a ferramenta
 **Sintaxe**

 Arquivo VsixColorCompiler \<XML> \<arquivo \<PkgDef>> Opcionais Args

 **Argumentos**

||||
|-|-|-|
|**Nome do switch**|**Observações**|**Obrigatório ou opcional**|
|Sem nome (arquivo.xml)|Este é o primeiro parâmetro sem nome e é o caminho para o arquivo XML converter.|Obrigatório|
|Sem nome (arquivo.pkgdef)|Este é o segundo parâmetro não nomeado e é o caminho de saída para o arquivo .pkgdef gerado.<br /><br /> Padrão: \<XML Filename>.pkgdef|Opcional|
|/noLogo|A configuração deste sinalizador impede a impressão de informações sobre produtos e direitos autorais.|Opcional|
|/?|Imprima informações de ajuda.|Opcional|
|/help|Imprima informações de ajuda.|Opcional|

 **Exemplos**

- VsixColorCompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef

- VsixColorCompiler D:\xml\colors.xml /noLogo

## <a name="notes"></a>Observações

- Esta ferramenta requer que a versão mais recente do tempo de execução VC++ seja instalada.

- Apenas arquivos únicos são suportados. A conversão em massa via caminhos de pasta não é suportada.

## <a name="sample-output"></a>Saída de exemplo
 O arquivo .pkgdef gerado pela ferramenta será semelhante às teclas abaixo:

```
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff

[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff
```
