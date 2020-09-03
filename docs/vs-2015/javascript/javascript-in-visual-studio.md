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
ms.openlocfilehash: 778912c3149f9f146c01dbab15afa4fabeaa49b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75852254"
---
# <a name="javascript-in-visual-studio"></a>JavaScript no Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O JavaScript é uma linguagem de primeira classe no Visual Studio. Você pode usar a maioria ou todos os auxílios de edição padrão (snippets de código IntelliSense, e assim por diante) ao escrever o código JavaScript no Visual Studio IDE. Você pode escrever código JavaScript para muitos tipos de aplicativos e serviços.

 Para obter a documentação de referência da linguagem JavaScript, consulte [JavaScript](https://msdn.microsoft.com/library/d1et7k7c\(v=vs.94\).aspx).

 Versões específicas do Visual Studio ou extensões específicas do Visual Studio podem ser necessárias para desenvolver serviços e tipos de aplicativo específicos usando HTML e JavaScript. A lista a seguir contém links para obtenção de mais informações.

- Para criar aplicativos de plataforma cruzada usando o Apache Cordova, [obtenha as Ferramentas do Visual Studio para Apache Cordova](https://taco.visualstudio.com/docs/install-vs-tools-apache-cordova/).

- Para criar aplicativos [da Windows Store](https://developer.microsoft.com/), [do Windows Phone](https://developer.microsoft.com/) e universais (que dão suporte a ambas as plataformas), [obtenha as ferramentas](https://developer.microsoft.com/windows/downloads).

- Para criar serviços baseados em nuvem, consulte o [site do Microsoft Azure](https://azure.microsoft.com/documentation/).

- Para criar sites e aplicativos Web, [consulte o site do ASP.NET](https://dotnet.microsoft.com/apps/aspnet/web-apps).

  > [!NOTE]
  > Você pode criar um site ASP.NET vazio e usá-lo para programação em HTML, CSS e JavaScript. O arquivo Webconfig fornecido pelo ASP.NET habilita a depuração no Visual Studio (ou você pode usar ferramentas F12 quando executa o aplicativo).

  O editor de JavaScript no Visual Studio fornece é compatível com o IntelliSense. Para obter mais informações, consulte [JavaScript IntelliSense](../ide/javascript-intellisense.md).

## <a name="whats-new-in-javascript"></a>Novidades no JavaScript
 Novas funcionalidades para JavaScript são listadas na tabela a seguir.

|Recurso|Descrição|
|-------------|-----------------|
|Classes|A nova sintaxe dá suporte a declaração de [classes](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/class).|
|Promises|[Promises](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Promise) permitem codificação assíncrona mais fácil e limpa. Construtores Promise têm suporte, juntamente com os métodos de utilitário `all` e `race`.|
|Iterators|Agora você pode iterar pelos objetos que permitem iteração (incluindo matrizes, objetos de tipo matriz e iteradores), invocando um gancho de iteração personalizado com as instruções a serem executadas para o valor de cada propriedade distinta. Para obter mais informações, consulte [Iteradores e geradores](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Iterators_and_Generators). **Observação:** ainda não há suporte para geradores.|
|Funções de seta|A função de seta (=>) fornece uma sintaxe abreviada para a palavra-chave `function`, que apresenta uma associação `this` léxica.|
|Novos métodos para objetos internos|Os objetos internos [Array](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Array), [Math](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Math), [Number](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Number), [Object](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object) e [String](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/String) incluem muitas novas propriedades e funções de utilitário para manipular e inspecionar dados.|
|Aprimoramentos de literal de objeto|Os objetos agora dão suporte a propriedades computadas, definições de método concisas e sintaxe abreviada para propriedades cujo valor é inicializado com uma variável de mesmo nome. Para obter mais informações, consulte [Criando objetos](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Object).|
|Proxies|[Proxies](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Proxy) habilitam o comportamento personalizado para objetos.|
|Parâmetros Rest|Parâmetros Rest permitem que você transforme argumentos consecutivos em uma chamada de função para uma matriz. Para obter mais informações, consulte [Funções](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function).|
|Operador de espalhamento|O [operador spread](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Operators/Spread_operator) ( `…` ) expande as expressões iterável em argumentos individuais. Por exemplo, `a.b(…array)` é aproximadamente o mesmo que `a.b.apply(a, array)`.|
|Símbolos|Os objetos [Symbol](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Symbol) permitem que sejam adicionadas propriedades aos objetos existentes sem a possibilidade de interferência com as propriedades do objeto existente, sem nenhuma visibilidade não intencional e sem outras adições não coordenadas por outro código.|
|Cadeias de caracteres de modelo|[Cadeias de caracteres de modelo](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Template_literals) são literais de cadeia de caracteres que permitem que expressões sejam avaliadas e concatenadas com o literal de cadeia de caracteres.|
|Aprimoramentos Unicode|Foram feitos aperfeiçoamentos ao suporte a Unicode. Por exemplo, um novo formato de sequência de escape dá suporte a pontos de código astral (pontos de código com mais de quatro dígitos hexadecimais). Para obter mais informações, consulte [Caracteres especiais](https://developer.mozilla.org/docs/Web/JavaScript/Guide/Regular_Expressions#Types_of_special_characters).|
|WeakSet|Um [WeakSet](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/WeakSet) será uma coleção de objetos que serão removidos pela coleta de lixo se não forem referenciados em nenhum outro lugar.|
