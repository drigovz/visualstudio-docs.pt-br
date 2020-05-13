---
title: 'Área de teste 8: Comutação plug-in | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], switching plug-ins
- source control plug-ins, switching
ms.assetid: 01370792-b5da-4e46-9ce2-7dd326587141
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 799fb04936a24004d73ce4c8aa3ec654490f3f62
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704389"
---
# <a name="test-area-8-plug-in-switching"></a>Área de teste 8: alternância de plug-in
O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente de desenvolvimento integrado (IDE) tem a interface do usuário (UI) para alterar o plug-in de controle de origem atual. Esta área de teste fornece casos de teste para o processo de seleção de qual plug-in usar para o controle da fonte da solução.

## <a name="command-menu-access"></a>Acesso ao menu de comando
 Os [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] seguintes caminhos do menu do ambiente de desenvolvimento integrado são usados nos casos de teste.

- Plug-in de controle de origem atual: **Opções de** -> **ferramentas** -> **Seleção de plug-in de****controle** -> de fonte .

- Vinculação do controle de origem de alteração: Controle de fonte**de controle de origem** -> de **origem** -> **de arquivo**...

## <a name="common-expected-behavior"></a>Comportamento Esperado Comum
 Alterar o plug-in de controle de origem para uma solução é possível sem sair do Visual Studio ou recarregar a solução. Além disso, o plug-in de controle de origem atual muda automaticamente para o usado por uma solução quando essa solução é carregada.

## <a name="test-cases"></a>Casos de teste
 A seguir, casos de teste específicos para a área de teste de comutação plug-in.

### <a name="case-8a-automatic-change"></a>Caso 8a: Mudança Automática

#### <a name="expected-behavior"></a>Comportamento esperado
 Quando um usuário carrega uma solução sob controle de origem, a solução é carregada automaticamente e o plug-in de controle de origem apropriado é selecionado como atual.

| Ação | Etapas de teste | Resultados esperados para verificar |
| - | - | - |
| Mudança automática de plug-in de controle de origem | 1. Selecione o plug-in em teste como atual **(Opções** -> **de ferramentas** -> **Seleção de plug-in de****controle** -> de fonte .)<br />2. Crie um novo projeto.<br />3. Adicione a solução ao controle de origem.<br />4. Selecione outro plug-in [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)](por exemplo, ).<br />5. Aceite o prompt da solução de descarga.<br />6. Reabrir a solução a partir do disco. | A solução está aberta.<br /><br /> O plug-in em teste é o plug-in de controle de origem atual. |

### <a name="case-8b-solution-based-change"></a>Caso 8b: Alteração baseada em solução

#### <a name="expected-behavior"></a>Comportamento esperado
 A solução pode ter seu plug-in de controle de origem associado alterado.

| Ação | Etapas de teste | Resultados esperados para verificar |
|----------------------------------| - | - |
| Mudança de plug-in para uma solução | 1. Selecione o plug-in em teste como atual **(Seleção** -> de**plug-in de controle** -> de fonte**de opções** -> **de ferramentas).**<br />2. Crie um novo projeto e solução.<br />3. Adicione a solução ao controle de origem.<br />4. Desvincular a solução do controle de origem (usando a caixa de diálogo **Alterar controle de origem).**<br />5. Selecione outro plug-in [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)](por exemplo, ).<br />6. Recarregue a solução do disco se descarregada.<br />7. Adicione a solução ao controle de origem.<br />8. Desvincular a solução do controle de origem (usando a caixa de diálogo **Alterar controle de** origem).<br />9. Selecione o plug-in em teste novamente.<br />10. Recarregue a solução do disco se descarregada.<br />11. Vincule a solução ao local original (usando a caixa de diálogo **Alterar controle de** origem). | A solução é adicionada ao controle de origem usando o plug-in selecionado. |

## <a name="see-also"></a>Confira também
- [Guia de teste para plug-ins de controle do código-fonte](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
