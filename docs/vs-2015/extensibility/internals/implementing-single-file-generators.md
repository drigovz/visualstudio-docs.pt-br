---
title: Implementando geradores de arquivo único | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- custom tools, implementing
- projects [Visual Studio SDK], extensibility
- projects [Visual Studio SDK], managed custom tools
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2ca842f05692d5d47ed42470f58f2be0bb45007
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192694"
---
# <a name="implementing-single-file-generators"></a>Implementando geradores de arquivo único
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Uma ferramenta personalizada, às vezes chamada de gerador de arquivo único, pode ser usada para estender o [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] e os [!INCLUDE[csprcs](../../includes/csprcs-md.md)] sistemas de projeto no [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Uma ferramenta personalizada é um componente COM que implementa a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interface. Usando essa interface, uma ferramenta personalizada transforma um único arquivo de entrada em um único arquivo de saída. O resultado da transformação pode ser o código-fonte ou qualquer outra saída que seja útil. Dois exemplos de arquivos de código gerados por ferramentas personalizados são gerados pelo código em resposta a alterações em um designer visual e arquivos gerados usando WSDL (Web Services Description Language).  
  
 Quando uma ferramenta personalizada é carregada ou o arquivo de entrada é salvo, o sistema de projeto chama o <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> método e passa uma referência a uma <xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> interface de retorno de chamada, na qual a ferramenta pode relatar seu progresso ao usuário.  
  
 O arquivo de saída gerado pela ferramenta personalizada é adicionado ao projeto com uma dependência no arquivo de entrada. O sistema de projeto determina automaticamente o nome do arquivo de saída, com base na cadeia de caracteres retornada pela implementação da ferramenta personalizada do <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> .  
  
 Uma ferramenta personalizada deve implementar a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> interface. Opcionalmente, as ferramentas personalizadas dão suporte à <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> interface para recuperar informações de fontes diferentes do arquivo de entrada. Em qualquer caso, antes de poder usar uma ferramenta personalizada, você deve registrá-la no sistema ou no [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Registro local. Para obter mais informações sobre como registrar ferramentas personalizadas, consulte [registrando geradores de arquivo único](../../extensibility/internals/registering-single-file-generators.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Determinando o namespace padrão de um projeto](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Expondo tipos para designers visuais](../../extensibility/internals/exposing-types-to-visual-designers.md)
