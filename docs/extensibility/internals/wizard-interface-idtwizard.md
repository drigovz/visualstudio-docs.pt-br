---
title: Interface do assistente (IDTWizard) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDTWizard interface
- wizards, interface
ms.assetid: 09618d9d-d115-45b6-bccc-de328994b39c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb1c8d728a76097321e4e1f16640cab97599d6ba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703271"
---
# <a name="wizard-interface-idtwizard"></a>Interface do assistente (IDTWizard)
O ambiente de desenvolvimento integrado <xref:EnvDTE.IDTWizard> (IDE) usa a interface para se comunicar com assistentes. Os assistentes devem implementar essa interface para serem instalados no IDE.

 O <xref:EnvDTE.IDTWizard.Execute%2A> método é o único <xref:EnvDTE.IDTWizard> método associado à interface. Os assistentes implementam este método e o IDE chama o método na interface. O exemplo a seguir mostra a assinatura do método.

```
/* IDTWizard Method */
STDMETHOD(Execute)(THIS_
   /* [in] */ IDispatch *Application,
   /* [in] */ long hwndOwner,
   /* [in] */ SAFEARRAY * *ContextParams,
   /* [in] */ SAFEARRAY * *CustomParams,
   /* [out] [in] */ wizardResult *RetVal
   );
```

 O mecanismo de partida é semelhante tanto para os **assistentes Novo Projeto** quanto para Adicionar Novos **Itens.** Para iniciar qualquer um <xref:EnvDTE.IDTWizard> dos dois, você chama a interface definida em Dteinternal.h. A única diferença é o conjunto de parâmetros de contexto e personalizados que são passados para a interface quando a interface é chamada.

 As informações a <xref:EnvDTE.IDTWizard> seguir descrevem a interface que [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] os assistentes devem implementar para trabalhar no IDE. O IDE <xref:EnvDTE.IDTWizard.Execute%2A> chama o método no assistente, passando-o o seguinte:

- O objeto DTE

     O objeto DTE é a raiz do modelo de Automação.

- A alça da caixa de diálogo da `hwndOwner ([in] long)`janela como mostrado no segmento de código, .

     O assistente `hwndOwner` usa isso como pai para a caixa de diálogo assistente.

- Os parâmetros de contexto passaram para a interface como `[in] SAFEARRAY (VARIANT)* ContextParams`variante para SAFEARRAY como mostrado no segmento de código, .

     Os parâmetros de contexto contêm uma matriz de valores específicos para o tipo de assistente que está sendo iniciado e o estado atual do projeto. O IDE passa os parâmetros de contexto para o assistente. Para obter mais informações, consulte [Parâmetros de contexto](../../extensibility/internals/context-parameters.md).

- Parâmetros personalizados passaram para a interface como uma variante para SAFEARRAY como mostrado no segmento de código, `[in] SAFEARRAY (VARIANT)* CustomParams`.

     Os parâmetros personalizados contêm uma matriz de parâmetros definidos pelo usuário. Um arquivo .vsz passa parâmetros personalizados para o IDE. Os valores são `Param=` determinados pelas declarações. Para obter mais informações, consulte [Parâmetros personalizados](../../extensibility/internals/custom-parameters.md).

- Os valores de retorno para a interface são

    ```
    wizardResultSuccess = -1,
    wizardResultFailure = 0
    wizardResultCancel = 1
    wizardResultBackout = 2
    ```

## <a name="see-also"></a>Confira também
- [Parâmetros de contexto](../../extensibility/internals/context-parameters.md)
- [Parâmetros personalizados](../../extensibility/internals/custom-parameters.md)
- [Assistentes](../../extensibility/internals/wizards.md)
- [Arquivo do assistente (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
