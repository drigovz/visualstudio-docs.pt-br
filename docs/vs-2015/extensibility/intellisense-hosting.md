---
title: Hospedagem do IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - IntelliSense hosting
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a5c378aec6822a436de0d8fc2656fcac7be4149f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203903"
---
# <a name="intellisense-hosting"></a>Hospedagem IntelliSense
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O Visual Studio habilita a hospedagem do IntelliSense. A hospedagem do IntellSense permite que você forneça IntelliSense para o código que não é hospedado pelo editor de texto do Visual Studio.  
  
## <a name="intellisense-hosting-usage"></a>Uso de hospedagem do IntelliSense  
 No Visual Studio, qualquer código que tenha acesso a um conjunto de conclusão e um buffer de texto pode obter janelas IntelliSense de qualquer lugar na interface do usuário. Alguns cenários de exemplo disso são conclusão na janela **Watch** ou no campo Condition de uma janela de propriedades de ponto de interrupção.  
  
### <a name="implementation-interfaces"></a>Interfaces de implementação  
  
#### <a name="ivsintellisensehost"></a>IVsIntellisenseHost  
 Qualquer componente da interface do usuário que hospede janelas pop-up do IntelliSense deve dar suporte à <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interface. A exibição de texto padrão do editor de núcleo inclui uma implementação de interface de estoque <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> para manter a funcionalidade atual do IntelliSense. Para a maior parte, os métodos da <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interface representam um subconjunto do que é implementado na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> interface. O subconjunto inclui manipulação de interface do usuário do IntelliSense, manipulação de interpolação e seleção e funcionalidade de substituição de texto simples. Além disso, a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interface permite o IntelliSense "Subject" e "Context" separados para que o IntelliSense possa ser fornecido para assuntos que não existem diretamente no buffer de texto que está sendo usado para o contexto.  
  
#### <a name="ivsintellisensehostgethostflags"></a>IVsIntellisenseHost.GetHostFlags  
 Um <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> provedor de interface deve implementar o <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A> método para permitir que um cliente determine que tipo de recursos do IntelliSense o host suporta.  
  
 Os sinalizadores de host, definidos em [IntelliSenseHostFlags](../extensibility/intellisensehostflags.md), são resumidos abaixo.  
  
|Sinalizador de host do IntelliSense|Descrição|  
|----------------------------|-----------------|  
|IHF_READONLYCONTEXT|Definir esse sinalizador significa que o buffer de contexto é somente leitura e a edição ocorre apenas dentro do texto do assunto.|  
|IHF_NOSEPERATESUBJECT|Definir esse sinalizador significa que não há nenhum assunto do IntelliSense separado. O assunto existe no buffer de contexto, como no <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> sistema IntelliSense tradicional.|  
|IHF_SINGLELINESUBJECT|A definição desse sinalizador significa que o assunto não é compatível com várias linhas, como em uma única edição de linha na janela de **inspeção** .|  
|IHF_FORCECOMMITTOCONTEXT|Se esse sinalizador for definido e o buffer de contexto precisar ser atualizado, o host permitirá que o sinalizador somente leitura no buffer de contexto seja ignorado e edite para continuar.|  
|IHF_OVERTYPE|A edição (no assunto ou no contexto) deve ser feita no modo sobrescrever.|  
  
#### <a name="ivsintellisensehostbeforecompletorcommit-and-ivsintellisensehostaftercompletorcommit"></a>IVsIntellisenseHost. BeforeCompletorCommit e IVsIntellisenseHost. AfterCompletorCommit  
 Esses métodos de retorno de chamada são chamados pela janela de conclusão antes e depois que o texto é confirmado, para habilitar o pré-processamento e o pós-processamento.  
  
#### <a name="ivsintellisensecompletor"></a>IVsIntellisenseCompletor  
 A <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor> interface é uma versão creatable da janela de conclusão padrão usada pelo IDE (ambiente de desenvolvimento integrado). Qualquer <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> interface pode implementar rapidamente o IntelliSense usando essa interface mais completo.  
  
## <a name="see-also"></a>Consulte Também  
 <xref:Microsoft.VisualStudio.TextManager.Interop>
