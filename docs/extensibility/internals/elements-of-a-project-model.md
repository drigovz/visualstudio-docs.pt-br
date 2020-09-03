---
title: Elementos de um modelo de projeto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf847e35878dc84bb32fe81053c01c23e565fc4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708531"
---
# <a name="elements-of-a-project-model"></a>Elementos de um modelo de projeto
As interfaces e implementações de todos os projetos no [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] compartilham uma estrutura básica: o modelo de projeto para o tipo de projeto. No modelo de projeto, que é o VSPackage que você está desenvolvendo, você cria objetos que estão em conformidade com suas decisões de design e trabalham em conjunto com a funcionalidade global fornecida pelo IDE. Embora você controle como um item de projeto é persistido, por exemplo, você não controla a notificação de que um arquivo deve ser persistido. Quando um usuário coloca o foco em um item de projeto aberto e escolhe **salvar** no menu **arquivo** na [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] barra de menus, o código do tipo de projeto deve interceptar o comando do IDE, persistir o arquivo e enviar a notificação de volta para o IDE que o arquivo não é mais alterado.

 Seu VSPackage interage com o IDE por meio de serviços que fornecem acesso às interfaces IDE. Por exemplo, por meio de serviços específicos, você monitora e roteia comandos e fornece informações de contexto para seleções feitas no projeto. Toda a funcionalidade global do IDE necessária para seu VSPackage é fornecida pelos serviços. Para obter mais informações sobre serviços, consulte [como: obter um serviço](../../extensibility/how-to-get-a-service.md).

 Outras considerações de implementação:

- Um único modelo de projeto pode conter mais de um tipo de projeto.

- Os tipos de projeto e as fábricas de projeto de atendedor são registrados independentemente com GUIDs.

- Cada projeto deve ter um arquivo de modelo ou Assistente para inicializar o novo arquivo de projeto quando um usuário cria um novo projeto por meio da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] interface do usuário. Por exemplo, os [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] modelos inicializam o que eventualmente se torna arquivos. vcproj.

  A ilustração a seguir mostra as interfaces primárias, os serviços e os objetos que compõem uma implementação de projeto típica. Você pode usar o auxiliar do aplicativo, `HierUtil7` , para criar os objetos subjacentes e outros textos de programação. Para obter mais informações sobre o `HierUtil7` auxiliar do aplicativo, consulte [usar classes de projeto HierUtil7 para implementar um tipo de projeto (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346).

  ![Gráfico de modelo de projeto do Visual Studio](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel") Modelo de projeto

  Para obter mais informações sobre as interfaces e os serviços listados no diagrama anterior e outras interfaces opcionais não incluídas no diagrama, consulte [Project Model Core Components](../../extensibility/internals/project-model-core-components.md).

  Os projetos podem dar suporte a comandos e, portanto, devem implementar a <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interface para participar do roteamento de comandos por meio dos GUIDs de contexto do comando.

## <a name="see-also"></a>Confira também
- [Lista de verificação: criar novos tipos de projeto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Usar classes de projeto HierUtil7 para implementar um tipo de projeto (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [Componentes principais do Project Model](../../extensibility/internals/project-model-core-components.md)
- [Criar instâncias de projeto usando fábricas de projeto](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
- [Como: obter um serviço](../../extensibility/how-to-get-a-service.md)
- [Criar tipos de projeto](../../extensibility/internals/creating-project-types.md)
