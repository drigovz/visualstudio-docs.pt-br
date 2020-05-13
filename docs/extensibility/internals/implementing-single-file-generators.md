---
title: Implementação de geradores de arquivos únicos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e700d09277edbb04b30676d3965b6c996d0a11f3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707651"
---
# <a name="implementing-single-file-generators"></a>Implementando geradores de arquivo único
Uma ferramenta personalizada - às vezes referida como um único [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] gerador de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]arquivos - pode ser usada para estender os sistemas e projetos em . Uma ferramenta personalizada é um componente <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> COM que implementa a interface. Usando esta interface, uma ferramenta personalizada transforma um único arquivo de entrada em um único arquivo de saída. O resultado da transformação pode ser o código fonte, ou qualquer outra saída que seja útil. Dois exemplos de arquivos de código gerados por ferramentas personalizadas são gerados em resposta a alterações em um designer visual e arquivos gerados usando o Web Services Description Language (WSDL).

 Quando uma ferramenta personalizada é carregada ou o arquivo de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> entrada é salvo, o <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> sistema de projeto chama o método e passa uma referência a uma interface de retorno de chamada, pela qual a ferramenta pode relatar seu progresso ao usuário.

 O arquivo de saída que a ferramenta personalizada gera é adicionado ao projeto com uma dependência do arquivo de entrada. O sistema de projeto determina automaticamente o nome do arquivo de saída, com base <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>na seqüência retornada pela implementação da ferramenta personalizada de .

 Uma ferramenta personalizada <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> deve implementar a interface. Opcionalmente, as ferramentas <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> personalizadas suportam a interface para recuperar informações de fontes diferentes do arquivo de entrada. Em qualquer caso, antes de usar uma ferramenta personalizada, você [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] deve registrá-la no sistema ou no registro local. Para obter mais informações sobre o registro de ferramentas [personalizadas, consulte Registrando Geradores de Arquivos Únicos](../../extensibility/internals/registering-single-file-generators.md).

## <a name="see-also"></a>Confira também
- [Expondo tipos para designers visuais](../../extensibility/internals/exposing-types-to-visual-designers.md)
