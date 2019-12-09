---
title: Personalizando o IntelliSense para RequireJS | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 2be07ef8-9c08-444b-a21a-22a4fe6386a3
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 279ac7737460c90f86918ae673e8f64ef1215546
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665889"
---
# <a name="customizing-intellisense-for-requirejs"></a>Personalizando o IntelliSense para RequireJS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A partir do Visual Studio 2013 Update 4, há suporte para o suporte para o conhecido arquivo JavaScript RequireJS e o carregador modular. O RequireJS facilita a definição de dependências entre módulos de código e a carga dinâmica de módulos somente quando necessário. Ao escrever código JavaScript que usa RequireJS, as sugestões do IntelliSense serão fornecidas para os módulos que você referenciou da definição do seu módulo ou referenciadas usando chamadas para `require()` de dentro do seu código.

 Por padrão, o Visual Studio dá suporte a uma configuração muito básica para dar suporte a RequireJS, mas é uma prática comum configurar suas próprias definições de configuração personalizadas (ou seja, definir aliases para bibliotecas). Este tópico descreve as diferentes maneiras que você pode personalizar o Visual Studio para trabalhar com a configuração exclusiva do seu projeto.

 Este tópico descreve como:

- Personalizar o RequireJS em projetos ASP.NET

- Personalizar o RequireJS em projetos JSProj, que são usados para criar Apache Cordova aplicativos, aplicativos da Windows Store e aplicativos HTML do LightSwitch

## <a name="customize-requirejs-in-aspnet-projects"></a>Personalizar o RequireJS em projetos ASP.NET
 O suporte para RequireJS é habilitado automaticamente quando um arquivo chamado require. js é referenciado pelo arquivo JavaScript atual (para obter mais informações, consulte a seção determinando o contexto do IntelliSense no [JavaScript IntelliSense](../ide/javascript-intellisense.md)). Em projetos ASP.NET, a referência a Requires. js normalmente é feita usando uma diretiva///\<reference/> dentro de um arquivo _references. js.

### <a name="configure-the-data-main-attribute-in-an-aspnet-project"></a>Configurar o atributo de dados-principal em um projeto ASP.NET
 Para simular com precisão como seu aplicativo funcionará quando você executá-lo, o editor de JavaScript precisará saber qual arquivo carregar primeiro ao configurar require. js. Isso normalmente é configurado no arquivo HTML do aplicativo usando o atributo `data-main` no elemento script que faz referência a Requires. js, como mostrado aqui.

```html
<script src="js/require.js" data-main="js/app.js"></script>
```

 Neste exemplo, o script referenciado por data-Main (JS/app. js) é carregado imediatamente após requerer. js. O arquivo que é carregado imediatamente é o melhor lugar para configurar primeiro o uso de RequireJS (usando `require.config()`). Para informar ao editor de JavaScript qual arquivo usar para `data-main` em seu aplicativo, adicione um atributo `data-main` e modifique uma diretiva///\<reference/> que referencie Requires. js em seu aplicativo. Por exemplo, você pode usar essa diretiva:

```javascript
/// <reference path="js/require.js" data-main="js/app.js" />
```

### <a name="configure-the-application-start-page-in-an-aspnet-project"></a>Configurar a página inicial do aplicativo em um projeto ASP.NET
 Quando o aplicativo é executado, o RequireJS assume que caminhos relativos para arquivos (por exemplo, ".. \\ "caminhos" são relativos ao arquivo HTML que carregou a biblioteca require. js. À medida que você escreve o código no editor do Visual Studio para um projeto ASP.NET, essa página inicial é desconhecida e você precisará informar ao editor qual página de início usar ao usar caminhos de arquivo relativos. Para fazer isso, adicione um atributo `start-page` à sua diretiva///\<reference/>.

```javascript
/// <reference path="js/require.js" data-main="js/app.js" start-page="/app/index.html" />
```

 O atributo `start-page` especifica a URL da página como você a veria em um navegador ao executar seu aplicativo.

## <a name="customize-requirejs-in-jsproj-projects"></a>Personalizar o RequireJS em projetos JSProj
 Os projetos JSProj (arquivos de projeto que terminam em uma extensão. JSProj) são usados ao criar aplicativos para Apache Cordova, aplicativos da Windows Store baseados em HTML ou aplicativos HTML do LightSwitch. Ao contrário dos projetos ASP.NET, esses projetos lêem referências a arquivos. js dos arquivos HTML existentes no projeto. Por isso, ao editar JavaScript em um projeto JSProj, você verá que o suporte para RequireJS está habilitado se o arquivo JavaScript que está sendo editado no momento for referenciado em outro arquivo HTML que também faz referência a require. js.

 As etapas de personalização necessárias para projetos ASP.NET não são necessárias em um arquivo de projeto JSProj. Ou seja, os arquivos de script usados pelo atributo `data-main` na marca de script que faz referência a require. js são carregados automaticamente para configurar o Requires. js. O arquivo HTML que faz referência a require. js também é usado como a página inicial do aplicativo.

## <a name="see-also"></a>Consulte também
 [JavaScript IntelliSense](../ide/javascript-intellisense.md)
