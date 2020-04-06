---
title: Parâmetros personalizados | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- wizards, custom parameters
- custom parameters
ms.assetid: ba5c364b-66e6-47ea-9760-a0b70de8f0a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cd52a49daa7d57a21d8cb0896f7108efa09e32b2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708943"
---
# <a name="custom-parameters"></a>Parâmetros personalizados
Parâmetros personalizados controlam a operação de um assistente após o início de um assistente. Um arquivo *.vsz* relacionado fornece uma matriz de parâmetros definidos pelo usuário que são embalados pelo ambiente de desenvolvimento integrado (IDE) e passados para o assistente como uma matriz de strings quando o assistente é iniciado. O assistente então analisa a matriz de strings e usa as informações para controlar o funcionamento real do assistente. Desta forma, um assistente pode personalizar a funcionalidade dependendo do conteúdo do arquivo *.vsz.*

 Os parâmetros de contexto, por outro lado, definem o estado do projeto quando o assistente é iniciado. Para obter mais informações, consulte [parâmetros de contexto](../../extensibility/internals/context-parameters.md).

 A seguir está um exemplo de um arquivo *.vsz* que tem parâmetros personalizados:

```
VSWIZARD 8.0
Wizard=VsWizard.VsWizard_Engine
Param="WIZARD_NAME = Sample Wizard"
Param="WIZARD_UI = FALSE"
Param="RELATIVE_PATH = VSWizards\Classwiz\ATL"
Param="PREPROCESS_FUNCTION = CanAddATLSupport"
Param="PROJECT_TYPE = CSPROJ"
```

 O autor do arquivo *.vsz* adiciona os valores dos parâmetros. Quando um usuário seleciona **Novo Projeto** ou Adicionar **Novo Item** no menu **Arquivo** ou clicando com o botão direito do mouse em um projeto no **Solution Explorer,** o IDE coleta esses valores em uma matriz de strings. Em seguida, o IDE <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.AddItem%2A> chama <xref:Microsoft.VisualStudio.Shell.Interop.VSADDITEMOPERATION> o método do projeto <xref:EnvDTE.IVsExtensibility.RunWizardFile%2A> com o conjunto de bandeiras, e o projeto chama o método responsável por executar o assistente e devolver o resultado.

 O assistente é responsável por analisar a matriz de strings e agir nas cordas apropriadamente. Desta forma, implementando parâmetros personalizados, você pode criar um assistente que executa uma variedade de funções. Em outras palavras, um assistente poderia ter três arquivos *.vsz* diferentes. Cada arquivo passa diferentes conjuntos de parâmetros personalizados para controlar o comportamento do assistente em várias situações.

 Para obter mais informações, consulte [arquivo Assistente (.vsz).](../../extensibility/internals/wizard-dot-vsz-file.md)

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- [Parâmetros de contexto](../../extensibility/internals/context-parameters.md)
- [Assistentes](../../extensibility/internals/wizards.md)
- [Arquivo Assistente (.vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
