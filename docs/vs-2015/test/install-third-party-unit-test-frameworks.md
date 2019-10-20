---
title: Instalar estruturas de teste de unidade de terceiros | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 47893b70-46f8-49dc-84bd-ec820178f683
caps.latest.revision: 12
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c2bd087dc0b06cbf8ffe4c08f84d819e8ef1c2f8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660522"
---
# <a name="install-third-party-unit-test-frameworks"></a>Instalar estruturas de teste de unidade de terceiros
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O Gerenciador de Testes do Visual Studio pode executar qualquer estrutura de teste de unidade que desenvolveu uma interface de adaptador para o Gerenciador. O programa de instalação da estrutura instala os binários e adiciona modelos de projeto do Visual Studio para os idiomas que ele dá suporte. Quando você cria um projeto com o modelo, a estrutura é registrada com o Gerenciador de Testes. Uma solução do Visual Studio pode conter projetos de teste de unidade que usam diferentes estruturas e que são direcionados em diferentes idiomas. O Gerenciador de Testes executa todos eles.

 **Requirements**

- Visual Studio Enterprise, Visual Studio Professional

## <a name="acquiring-third-party-frameworks"></a>Aquisição de estruturas de terceiros
 Você pode baixar e instalar diversas estruturas de teste de unidade de terceiros usando o Gerenciador de extensões do Visual Studio ou da Galeria do Visual Studio no site do MSDN. Estruturas também podem ser baixadas de outros sites, como o site da estrutura.

### <a name="installing-from-visual-studio"></a>Instalação do Visual Studio

1. Escolha **Ferramentas** no menu padrão e, em seguida, selecione **Extensões e atualizações**.

2. Expanda **Online**, **Galeria do Visual Studio**, **Ferramentas**. Escolha **Teste**.

3. Navegue pela lista para localizar a estrutura.

4. Selecione a estrutura e escolha **Download**.

   Para obter mais informações, consulte [Localizando e Usando Extensões do Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

### <a name="installing-from-the-web"></a>Instalação da Web
 Se você souber a estrutura em que você está interessado:

1. Abra [Visual Studio Marketplace](https://marketplace.visualstudio.com).

2. Digite o nome da estrutura na caixa **Localizar**.

3. Escolha a estrutura na lista de resultados para navegar até a página da Galeria do Visual Studio para a ferramenta.

   Para procurar uma lista de estruturas juntamente com outras ferramentas de teste:

4. Abra [Visual Studio Marketplace](https://marketplace.visualstudio.com).

5. Escolha **Procurar**.

6. Na lista **Categoria**, expanda o nó **Ferramentas** e escolha **Teste**.

7. Escolha uma estrutura na lista de resultados para navegar até uma página da Galeria do Visual Studio para a ferramenta.

## <a name="see-also"></a>Consulte também
 [Efetuar teste de unidade em seu código](../test/unit-test-your-code.md)
