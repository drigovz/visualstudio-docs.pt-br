---
title: Atualizando a Interface do Usuário | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces, updating
- commands, updating UI
ms.assetid: 376e2f56-e7bf-4e62-89f5-3dada84a404b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1c51ae790eb35645fbe9aec5d9c422e1051aaa69
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698881"
---
# <a name="updating-the-user-interface"></a>Atualizando a interface do usuário
Depois de implementar um comando, você pode adicionar código para atualizar a interface do usuário com o estado de seus novos comandos.

 Em um aplicativo típico do Win32, o conjunto de comandos pode ser continuamente pesquisado e o estado dos comandos individuais pode ser ajustado à medida que o usuário os vê. No entanto, como o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] shell pode hospedar um número ilimitado de VSPackages, uma votação extensiva pode diminuir a capacidade de resposta, especialmente a votação entre as assembléias interop entre código gerenciado e COM.

### <a name="to-update-the-ui"></a>Para atualizar a ui

1. Execute uma das seguintes etapas:

    - Chame o método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> .

         Uma <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> interface pode ser <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> obtida a partir do serviço, da seguinte forma.

        ```csharp
        void UpdateUI(Microsoft.VisualStudio.Shell.ServiceProvider sp)
        {
            IVsUIShell vsShell = (IVsUIShell)sp.GetService(typeof(IVsUIShell));
            if (vsShell != null)
            {
                int hr = vsShell.UpdateCommandUI(0);
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);
            }
        }

        ```

         Se o parâmetro <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> do não for`TRUE`zero ( ), então a atualização é realizada de forma sincronizada e imediata. Recomendamos que você`FALSE`passe zero () para este parâmetro para ajudar a manter o bom desempenho. Se você quiser evitar o `DontCache` cache, aplique o sinalizador quando criar o comando no arquivo .vsct. No entanto, use a bandeira com cautela ou o desempenho pode diminuir. Para obter mais informações sobre bandeiras de comando, consulte a documentação [do Elemento de Bandeira de Comando.](../extensibility/command-flag-element.md)

    - Em VSPackages que hospedam um controle ActiveX usando o modelo de ativação no <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> local em uma janela, pode ser mais conveniente usar o método. O <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.UpdateCommandUI%2A> método <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> na interface <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager.UpdateUI%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> o método na interface são funcionalmente equivalentes. Ambos fazem com que o ambiente re-consulta o estado de todos os comandos. Normalmente, uma atualização não é realizada imediatamente. Em vez disso, uma atualização é adiada até o tempo ocioso. O shell armazena o estado de comando para ajudar a manter o bom desempenho. Se você quiser evitar o `DontCache` cache, aplique o sinalizador quando criar o comando no arquivo .vsct. No entanto, use a bandeira com cautela porque o desempenho pode diminuir.

         Observe que você <xref:Microsoft.VisualStudio.Shell.Interop.IOleInPlaceComponentUIManager> pode obter `QueryInterface` a interface <xref:Microsoft.VisualStudio.Shell.Interop.IOleComponentUIManager> chamando o método <xref:Microsoft.VisualStudio.Shell.Interop.SOleComponentUIManager> em um objeto ou obtendo a interface do serviço.

## <a name="see-also"></a>Confira também
- [Como os VSPackages adicionam elementos da interface do usuário](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Implementação](../extensibility/internals/command-implementation.md)
