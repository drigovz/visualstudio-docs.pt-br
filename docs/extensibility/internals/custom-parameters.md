---
title: Parâmetros personalizados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a879c7a842bdabff396fa2df31d0aa7326b19c50
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312209"
---
# <a name="custom-parameters"></a>Parâmetros personalizados
Parâmetros personalizados controlam a operação de um assistente depois de um assistente foi iniciado. Um relacionados *. vsz* arquivo fornece uma matriz de parâmetros definidos pelo usuário que são empacotados pelo ambiente de desenvolvimento integrado (IDE) e passado para o assistente como uma matriz de cadeias de caracteres quando o assistente for iniciado. Em seguida, o assistente analisa a matriz de cadeias de caracteres e usa as informações para controlar a operação real do assistente. Dessa forma, um assistente pode personalizar a funcionalidade dependendo do conteúdo do *. vsz* arquivo.

 Parâmetros de contexto, por outro lado, definem o estado do projeto quando o assistente for iniciado. Para obter mais informações, consulte [parâmetros de contexto](../../extensibility/internals/context-parameters.md).

 A seguir está um exemplo de uma *. vsz* arquivo que tem parâmetros personalizados:

```
VSWIZARD 8.0
Wizard=VsWizard.VsWizard_Engine
Param="WIZARD_NAME = Sample Wizard"
Param="WIZARD_UI = FALSE"
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"
Param="PREPROCESS_FUNCTION = CanAddATLSupport"
Param="PROJECT_TYPE = CSPROJ"
```

 O autor do *. vsz* arquivo adiciona os valores dos parâmetros. Quando um usuário seleciona **novo projeto** ou **Adicionar Novo Item** sobre o **arquivo** menu ou clicando em um projeto no **Gerenciador de soluções**, o IDE coleta esses valores em uma matriz de cadeias de caracteres. O IDE, em seguida, chama o projeto <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> método com o <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> sinalizador conjunto e as chamadas de projeto a <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> método que é responsável por executar o assistente e retornar o resultado.

 O assistente é responsável por analisar a matriz de cadeias de caracteres e agir sobre as cadeias de caracteres corretamente. Dessa forma, com a implementação de parâmetros personalizados, você pode criar um assistente que executa uma variedade de funções. Em outras palavras, um assistente poderia ter três diferentes *. vsz* arquivos. Cada arquivo passa a diferentes conjuntos de parâmetros personalizados para controlar o comportamento do assistente em várias situações.

 Para obter mais informações, consulte [arquivo do assistente (. vsz)](../../extensibility/internals/wizard-dot-vsz-file.md).

## <a name="see-also"></a>Consulte também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- [Parâmetros de contexto](../../extensibility/internals/context-parameters.md)
- [Assistentes:](../../extensibility/internals/wizards.md)
- [Arquivo do assistente (. vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)