---
title: Atribua GUIDs específicos aos assinantes do Visual Studio | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 04/20/2020
ms.topic: conceptual
description: Saiba como os administradores podem fazer uma assinatura específica do GUID para assinantes
ms.openlocfilehash: e2e8cd4f5d07f218fc23c0b7b6f28ababc25263f
ms.sourcegitcommit: 0b8497b720eb06bed8ce2194731177161b65eb84
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82072587"
---
# <a name="assign-specific-subscriptions-in-the-visual-studio-subscriptions-administration-portal"></a>Atribua assinaturas específicas no Portal de Administração de Assinaturas do Visual Studio

Os administradores agora podem usar o Portal de Administração de Assinaturas do Visual Studio para atribuir assinaturas específicas a assinantes individuais.  Isso pode ser útil em situações em que a organização possui funcionários temporários ou fornecedores que precisam ter acesso a uma assinatura por um curto período.  Os administradores podem atribuir uma assinatura que já foi parcialmente usada, deixando suas novas assinaturas para uso a longo prazo.  

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4t4cl]


## <a name="assign-specific-subscription-guids-to-users"></a>Atribuir GUIDs de assinatura específicos aos usuários

O processo de atribuição de assinaturas específicas a indivíduos envolve aproveitar dois processos de administração existentes para atribuir guids (Guias) globalmente exclusivos a usuários individuais.  O processo de três etapas inclui exportar uma lista de suas assinaturas e atribuições atuais, usando essa lista para identificar os GUIDs específicos que você deseja atribuir e, em seguida, usando o processo de adicionar em massa para carregar as novas atribuições.

### <a name="export-your-subscriptions-information"></a>Exporte suas informações de assinaturas

Para executar a exportação:
1. Entre no [portal de administração](https://manage.visualstudio.com).
2. Selecione a guia **Exportar** e o arquivo será baixado no computador local. O arquivo inclui o nome da conta do contrato que contém suas assinaturas do usuário e também a data da exportação.
> [!div class="mx-imgBorder"]
> ![Exportar assinantes](_img/exporting-subscriptions/exporting-subscriptions.png)

### <a name="identify-the-guids-you-want-to-assign"></a>Identifique os GUIDs que você deseja atribuir

Se você já usou a ferramenta Exportar anteriormente, você notará que novos campos foram adicionados à planilha produzida.  Isso ajudará você a determinar o status de cada assinatura e quais você deseja atribuir aos usuários.  

- **Status da assinatura**: Este campo indicará "atribuído" ou "não atribuído".  Se uma assinatura tiver um status de "atribuído", ela também terá informações do usuário associadas a ela, como nome, e-mail, etc. 
- **Status de uso**: O status de uso indicará "novo", o que significa que nunca foi atribuído a um usuário ou "usado" o que indica que foi atribuído a um usuário em algum momento.  

Você pode usar os valores nesses campos, juntamente com outras informações na planilha para determinar quais assinaturas você deseja atribuir a usuários individuais. Você pode aplicar um filtro no Excel para ajudar a reduzir a lista por status, nível de assinatura, data de validade, etc. 

### <a name="upload-your-new-assignments"></a>Faça upload de suas novas atribuições

O passo final é baixar o modelo **Bulk add,** preencher as informações necessárias para as assinaturas que você deseja atribuir e fazer upload do modelo.  Para obter uma descrição completa desse processo, consulte nosso artigo [Adicionar vários usuários.](assign-license-bulk.md)  

> [!IMPORTANT]
> Para garantir um upload bem-sucedido, certifique-se de que:
> - Você está usando o modelo vinculado na caixa de diálogo quando você **seleciona Adicionar em massa**.  Não use uma cópia armazenada localmente do modelo, pois ele pode não conter todos os campos necessários.  O uso de um modelo antigo fará com que o upload falhe. 
> - Todos os campos mostrados como **Exigidos** no modelo estão completos.
> - Não há erros listados na coluna **Mensagem de erro.**
> - Cada GUID é usado apenas uma vez no modelo. 
> - O nível de assinatura no modelo corresponde à assinatura do GUID na lista exportada. 
> - O GUID ainda não está atribuído a outro usuário na lista exportada. 

## <a name="frequently-asked-questions"></a>Perguntas frequentes
### <a name="qhow-do-i-change-which-subscription-is-currently-assigned-to-an-individual-user"></a>P: Como altero qual assinatura é atualmente atribuída a um usuário individual?
R: Se você quiser alterar qual GUID é atribuído a um usuário, você deve primeiro excluir a assinatura desse usuário.  Para obter mais informações, consulte nosso artigo [Delete assinaturas](delete-license.md) para obter mais informações.  Depois de excluir a assinatura para esse usuário, use o processo descrito acima para exportar a lista e carregar as novas informações de assinatura.  

## <a name="see-also"></a>Confira também
- [Documentação do Visual Studio](/visualstudio/)
- [Documentação do Azure DevOps](/azure/devops/)
- [Documentação do Azure](/azure/)
- [Documentação do Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Próximas etapas
Agora que você atribuiu assinaturas aos usuários, descubra como executar outras tarefas administrativas.
- [Atribuir assinaturas individuais](assign-license.md)
- [Atribuir várias assinaturas](assign-license-bulk.md)
- [Editar assinaturas](edit-license.md)
- [Excluir assinaturas](delete-license.md)
- [Determine o uso máximo](maximum-usage.md)


