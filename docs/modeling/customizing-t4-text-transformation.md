---
title: Personalizando transformação de texto T4
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 03acd2b989f3403c04d7a0bacdf1fb3e6e6213db
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71251834"
---
# <a name="customize-t4-text-transformation"></a>Personalizar a transformação de texto T4

Os modelos de texto são um recurso do Visual Studio que permite gerar código de programa ou outros arquivos de texto por meio de um processo de transformação. Usando [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)]o, você pode estender o processo de transformação de modelo padrão Personalizando o processador de diretiva de modelo de texto ou o host de modelo de texto.

## <a name="in-this-section"></a>Nesta seção

 [O processo de transformação do modelo de texto](../modeling/the-text-template-transformation-process.md) Descreve como funciona a transformação de texto e explica a função do host de modelo e os processadores de diretiva.

 [Criando processadores de diretiva de modelo de texto T4 personalizados](../modeling/creating-custom-t4-text-template-directive-processors.md) O processador de diretiva lida com diretivas em seu modelo, `<#@template#>.` como é executado durante a compilação do modelo, e pode carregar assemblies e outros recursos. Ele também pode inserir código que carregará recursos em tempo de execução. Ao definir seu próprio processador de diretiva, você pode reduzir a complexidade de seus modelos.

 [Invocando a transformação de texto em uma extensão do vs](../modeling/invoking-text-transformation-in-a-vs-extension.md) Se você estiver escrevendo uma extensão do Visual Studio, como um comando de menu ou manipulador de eventos, sua extensão poderá usar o serviço de modelagem de texto para transformar qualquer modelo de texto. Você pode passar dados de parâmetro para o modelo usando o objeto de sessão e obter os valores de dentro do modelo usando a `<#@parameter#>` diretiva.

 [Processando modelos de texto usando um host personalizado](../modeling/processing-text-templates-by-using-a-custom-host.md) Quando o código do modelo de texto é executado, o host fornece acesso a arquivos externos e ao estado do aplicativo. Por exemplo, o host que executa as transformações de texto no Visual Studio pode fornecer acesso a **Gerenciador de soluções**. Ele também exibe erros na janela de mensagem de erro. Se você quiser executar transformações de texto em um contexto diferente, poderá definir seu próprio host que fornece acesso aos serviços disponíveis nesse contexto.

 Se você estiver escrevendo uma extensão do Visual Studio, considere usar o serviço de transformação de texto existente em vez de escrever seu próprio host. Para obter mais informações, consulte [invocando a transformação de texto em uma extensão do vs](../modeling/invoking-text-transformation-in-a-vs-extension.md).

## <a name="reference"></a>Referência

- [Escrever um modelo de texto T4](../modeling/writing-a-t4-text-template.md) fornece a sintaxe de diretivas de modelo de texto e blocos de controle.