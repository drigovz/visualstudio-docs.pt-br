---
title: Implementando geradores de arquivo único | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 69bde665e62d063b6bab8784634777eeea02e941
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727170"
---
# <a name="implementing-single-file-generators"></a>Implementando geradores de arquivo único
Uma ferramenta personalizada, às vezes chamada de gerador de arquivo único, pode ser usada para estender o [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] e [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] sistemas de projeto no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Uma ferramenta personalizada é um componente COM que implementa a interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>. Usando essa interface, uma ferramenta personalizada transforma um único arquivo de entrada em um único arquivo de saída. O resultado da transformação pode ser o código-fonte ou qualquer outra saída que seja útil. Dois exemplos de arquivos de código gerados por ferramentas personalizados são gerados pelo código em resposta a alterações em um designer visual e arquivos gerados usando WSDL (Web Services Description Language).

 Quando uma ferramenta personalizada é carregada ou o arquivo de entrada é salvo, o sistema de projeto chama o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> e passa uma referência a uma interface de retorno de chamada <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress>, na qual a ferramenta pode relatar seu progresso ao usuário.

 O arquivo de saída gerado pela ferramenta personalizada é adicionado ao projeto com uma dependência no arquivo de entrada. O sistema de projeto determina automaticamente o nome do arquivo de saída, com base na cadeia de caracteres retornada pela implementação da ferramenta personalizada de <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>.

 Uma ferramenta personalizada deve implementar a interface <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>. Opcionalmente, as ferramentas personalizadas dão suporte à interface <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> para recuperar informações de fontes diferentes do arquivo de entrada. Em qualquer caso, antes de poder usar uma ferramenta personalizada, você deve registrá-la no sistema ou no registro local [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Para obter mais informações sobre como registrar ferramentas personalizadas, consulte [registrando geradores de arquivo único](../../extensibility/internals/registering-single-file-generators.md).

## <a name="see-also"></a>Consulte também
- [Expor tipos aos designers visuais](../../extensibility/internals/exposing-types-to-visual-designers.md)