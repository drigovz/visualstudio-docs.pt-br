---
title: Personalizando transformação de texto T4 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, API
- text templates, custom hosts
ms.assetid: 62cd9a3c-a6e1-4b29-93f5-f2a0cf47dc92
caps.latest.revision: 30
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: ea2881cfebaf10d7a72e8651214cf3a6f64debae
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58926369"
---
# <a name="customizing-t4-text-transformation"></a>Personalizando transformação de texto T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Modelos de texto são um recurso do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] que permitem que você gerar o código do programa ou outros arquivos de texto por meio de um processo de transformação. Usando [!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)], você pode estender o processo de transformação de modelo padrão, personalizando o processador de diretriz de modelo de texto ou o host de modelo de texto.  
  
## <a name="in-this-section"></a>Nesta seção  
 [O processo de transformação de modelo de texto](../modeling/the-text-template-transformation-process.md)  
 Descreve como a transformação de texto funciona e explica a função de host de modelo e os processadores de diretriz.  
  
 [Criando processadores de diretiva de modelo de texto T4 personalizados](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 O processador de diretriz lida com diretivas em seu modelo, tal como `<#@template#>.` ele é executado durante a compilação do modelo e pode carregar assemblies e outros recursos. Ele também pode inserir o código que irá carregar recursos em tempo de execução. Ao definir seu próprio processador de diretriz, você pode reduzir a complexidade de seus modelos.  
  
 [Invocando transformação de texto em uma extensão do VS](../modeling/invoking-text-transformation-in-a-vs-extension.md)  
 Se você estiver escrevendo um [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] extensão como um manipulador de evento ou comando de menu, a sua extensão pode usar o serviço de modelagem de texto para transformar qualquer modelo de texto. Você pode passar dados de parâmetro para o modelo usando o objeto de sessão e obter os valores de dentro do modelo usando o `<#@parameter#>` diretiva.  
  
 [Processando modelos de texto usando um host personalizado](../modeling/processing-text-templates-by-using-a-custom-host.md)  
 Quando o código do modelo de texto é executado, o host fornece acesso a arquivos externos e o estado do aplicativo. Por exemplo, o host que executa transformações de texto em [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] pode fornecer acesso ao Gerenciador de soluções. Ele também exibe os erros na janela de mensagem de erro. Se você quiser executar transformações de texto em um contexto diferente, você pode definir seu próprio host que fornece acesso aos serviços disponíveis nesse contexto.  
  
 Se você estiver escrevendo um [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] extensão, considere usar o serviço de transformação de texto existente em vez de escrever seu próprio host. Para obter mais informações, consulte [invocando transformação de texto em uma extensão do VS](../modeling/invoking-text-transformation-in-a-vs-extension.md).  
  
## <a name="reference"></a>Referência  
 [Gravando um modelo de texto T4](../modeling/writing-a-t4-text-template.md)  
  
 Fornece a sintaxe de diretivas de modelo de texto e blocos de controle.
