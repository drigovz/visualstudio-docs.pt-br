---
title: JavaScript
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-javascript
ms.topic: conceptual
ms.assetid: f3eee13e-30e4-4bc1-81f5-058d7e379b75
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 962657d19026f85e98b1f1d22241aa57013d7df6
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2019
ms.locfileid: "54834066"
---
# <a name="javascript-in-visual-studio"></a>JavaScript no Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O JavaScript é uma linguagem de primeira classe no Visual Studio. Você pode usar a maioria ou todos os auxílios de edição padrão (snippets de código IntelliSense, e assim por diante) ao escrever o código JavaScript no Visual Studio IDE. Você pode escrever código JavaScript para muitos tipos de aplicativos e serviços.

 Para obter a documentação de referência da linguagem JavaScript, consulte [JavaScript](http://msdn.microsoft.com/library/d1et7k7c\(v=vs.94\).aspx).

 Versões específicas do Visual Studio ou extensões específicas do Visual Studio podem ser necessárias para desenvolver serviços e tipos de aplicativo específicos usando HTML e JavaScript. A lista a seguir contém links para obtenção de mais informações.

- Para criar aplicativos de plataforma cruzada usando o Apache Cordova, [obtenha as Ferramentas do Visual Studio para Apache Cordova](http://go.microsoft.com/fwlink/p/?LinkId=397606).

- Para criar aplicativos [da Windows Store](http://dev.windows.com/develop), [do Windows Phone](http://dev.windows.com/develop) e universais (que dão suporte a ambas as plataformas), [obtenha as ferramentas](http://dev.windows.com/develop/downloads).

- Para criar serviços baseados em nuvem, consulte o [site do Microsoft Azure](http://azure.microsoft.com/documentation/).

- Para criar sites e aplicativos Web, [consulte o site do ASP.NET](http://www.asp.net/get-started/websites).

  > [!NOTE]
  >  Você pode criar um site ASP.NET vazio e usá-lo para programação em HTML, CSS e JavaScript. O arquivo Webconfig fornecido pelo ASP.NET habilita a depuração no Visual Studio (ou você pode usar ferramentas F12 quando executa o aplicativo).

  O editor de JavaScript no Visual Studio fornece é compatível com o IntelliSense. Para obter mais informações, consulte [JavaScript IntelliSense](../ide/javascript-intellisense.md).

## <a name="whats-new-in-javascript"></a>Novidades no JavaScript
 Novas funcionalidades para JavaScript são listadas na tabela a seguir.

|Recurso|Descrição|
|-------------|-----------------|
|Classes|A nova sintaxe dá suporte a declaração de [classes](/visualstudio/scripting-docs/javascript/reference/class-statement-javascript).|
|Promises|[Promises](/visualstudio/scripting-docs/javascript/reference/promise-object-javascript) permitem codificação assíncrona mais fácil e limpa. Construtores Promise têm suporte, juntamente com os métodos de utilitário `all` e `race`.|
|Iterators|Agora você pode iterar pelos objetos que permitem iteração (incluindo matrizes, objetos de tipo matriz e iteradores), invocando um gancho de iteração personalizado com as instruções a serem executadas para o valor de cada propriedade distinta. Para obter mais informações, consulte [Iteradores e geradores](/visualstudio/scripting-docs/javascript/advanced/iterators-and-generators-javascript). **Observação:**  Ainda não há suporte para geradores.|
|Funções de seta|A função de seta (=>) fornece uma sintaxe abreviada para a palavra-chave `function`, que apresenta uma associação `this` léxica.|
|Novos métodos para objetos internos|Os objetos internos [Array](/visualstudio/scripting-docs/javascript/reference/array-object-javascript), [Math](/visualstudio/scripting-docs/javascript/reference/math-object-javascript), [Number](/visualstudio/scripting-docs/javascript/reference/number-object-javascript), [Object](/visualstudio/scripting-docs/javascript/reference/object-object-javascript) e [String](/visualstudio/scripting-docs/javascript/reference/string-object-javascript) incluem muitas novas propriedades e funções de utilitário para manipular e inspecionar dados.|
|Aprimoramentos de literal de objeto|Os objetos agora dão suporte a propriedades computadas, definições de método concisas e sintaxe abreviada para propriedades cujo valor é inicializado com uma variável de mesmo nome. Para obter mais informações, consulte [Criando objetos](/visualstudio/scripting-docs/javascript/creating-objects-javascript).|
|Proxies|[Proxies](/visualstudio/scripting-docs/javascript/reference/proxy-object-javascript) habilitam o comportamento personalizado para objetos.|
|Parâmetros Rest|Parâmetros Rest permitem que você transforme argumentos consecutivos em uma chamada de função para uma matriz. Para obter mais informações, consulte [Funções](/visualstudio/scripting-docs/javascript/functions-javascript).|
|Operador de espalhamento|O [operador de espalhamento](/visualstudio/scripting-docs/javascript/reference/spread-operator-decrement-dot-dot-dot-javascript) (`…`) expande expressões que podem ser iteradas, transformando-as em argumentos individuais. Por exemplo, `a.b(…array)` é aproximadamente o mesmo que `a.b.apply(a, array)`.|
|Símbolos|Os objetos [Symbol](/visualstudio/scripting-docs/javascript/reference/symbol-object-javascript) permitem que sejam adicionadas propriedades aos objetos existentes sem a possibilidade de interferência com as propriedades do objeto existente, sem nenhuma visibilidade não intencional e sem outras adições não coordenadas por outro código.|
|Cadeias de caracteres de modelo|[Cadeias de caracteres de modelo](/visualstudio/scripting-docs/javascript/advanced/template-strings-javascript) são literais de cadeia de caracteres que permitem que expressões sejam avaliadas e concatenadas com o literal de cadeia de caracteres.|
|Aprimoramentos Unicode|Foram feitos aperfeiçoamentos ao suporte a Unicode. Por exemplo, um novo formato de sequência de escape dá suporte a pontos de código astral (pontos de código com mais de quatro dígitos hexadecimais). Para obter mais informações, consulte [Caracteres especiais](/visualstudio/scripting-docs/javascript/advanced/special-characters-javascript).|
|WeakSet|Um [WeakSet](/visualstudio/scripting-docs/javascript/reference/weakset-object-javascript) será uma coleção de objetos que serão removidos pela coleta de lixo se não forem referenciados em nenhum outro lugar.|
