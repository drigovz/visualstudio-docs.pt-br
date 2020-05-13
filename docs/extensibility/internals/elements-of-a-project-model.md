---
title: Elementos de um Modelo de Projeto | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708531"
---
# <a name="elements-of-a-project-model"></a>Elementos de um modelo de projeto
As interfaces e implementações [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de todos os projetos compartilham uma estrutura básica: o modelo de projeto para o seu tipo de projeto. No seu modelo de projeto, que é o VSPackage que você está desenvolvendo, você cria objetos que cumprem suas decisões de design e trabalham em conjunto com a funcionalidade global fornecida pelo IDE. Embora você controle como um item de projeto é persistido, por exemplo, você não controla a notificação de que um arquivo deve ser persistido. Quando um usuário coloca o foco em um item de projeto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] aberto e escolhe **Salvar** no menu **Arquivo** na barra de menu, seu código de tipo de projeto deve interceptar o comando do IDE, persistir o arquivo e enviar a notificação de volta ao IDE de que o arquivo não está mais alterado.

 Seu VSPackage interage com o IDE através de serviços que fornecem acesso às interfaces IDE. Por exemplo, através de serviços específicos, você monitora e roteia comandos e fornece informações de contexto para seleções feitas no projeto. Toda a funcionalidade global de IDE necessária para o seu VSPackage é fornecida por serviços. Para obter mais informações sobre serviços, consulte [Como: Obter um serviço](../../extensibility/how-to-get-a-service.md).

 Outras considerações de implementação:

- Um único modelo de projeto pode conter mais de um tipo de projeto.

- Os tipos de projetos e as fábricas de projetos atendentes são registrados independentemente com GUIDs.

- Cada projeto deve ter um arquivo de modelo ou assistente para inicializar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] o novo arquivo de projeto quando um usuário cria um novo projeto através da interface do usuário. Por exemplo, [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] os modelos inicializam o que eventualmente se torna arquivos .vcproj.

  A ilustração a seguir mostra as interfaces primárias, serviços e objetos que compõem uma implementação típica do projeto. Você pode usar o `HierUtil7`ajudante de aplicativo, para criar os objetos subjacentes e outras caldeiras de programação. Para obter mais `HierUtil7` informações sobre o ajudante de aplicativo, consulte [Use HierUtil7 classes de projeto para implementar um tipo de projeto (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346).

  ![Visual Studio modelo de projeto gráfico](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel") Modelo de projeto

  Para obter mais informações sobre as interfaces e serviços listados no diagrama anterior e outras interfaces opcionais não incluídas no diagrama, consulte [componentes do núcleo do modelo do Projeto](../../extensibility/internals/project-model-core-components.md).

  Os projetos podem suportar comandos <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> e, portanto, devem implementar a interface para participar do roteamento de comandoatravés dos GUIDs do contexto de comando.

## <a name="see-also"></a>Confira também
- [Checklist: Crie novos tipos de projetos](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Use classes de projeto HierUtil7 para implementar um tipo de projeto (C++)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [Componentes do núcleo do modelo de projeto](../../extensibility/internals/project-model-core-components.md)
- [Criar instâncias de projeto usando fábricas de projetos](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
- [Como: Obter um serviço](../../extensibility/how-to-get-a-service.md)
- [Criar tipos de projeto](../../extensibility/internals/creating-project-types.md)
