---
title: Quando criar tipos de projeto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5b5bc2bacb53973bd552b983b742e4f9e68fe31b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687707"
---
# <a name="when-to-create-project-types"></a>Quando criar tipos de projeto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A criação de um novo tipo de projeto fornece uma base para personalizar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] os usuários. No entanto, a criação de um novo tipo de projeto não é necessária para todas as [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] personalizações. As diretrizes a seguir devem ajudá-lo a determinar se um novo tipo de projeto é necessário para seu cenário.  
  
## <a name="create-a-new-project-type"></a>Criar um novo tipo de projeto  
 Você deve criar um tipo de projeto se quiser personalizar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] o para agir de uma ou mais das seguintes maneiras:  
  
- Participe de compilação, implantação, configurações e controle do código-fonte.  
  
- Oferecer suporte à depuração.  
  
- Exibir itens de projeto no **Gerenciador de soluções**.  
  
- Use a caixa de diálogo **Abrir projeto** ou **novo projeto** .  
  
- Suporte a aninhamento de projetos.  
  
## <a name="extend-an-existing-project-type"></a>Estender um tipo de projeto existente  
 Talvez você queira criar um novo tipo de projeto que possa ser usado [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nas seguintes maneiras de modificar ou estender o comportamento de um tipo de projeto existente, por exemplo, modificar o processo de compilação para [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] projetos:  
  
- Trabalhe com vários arquivos como uma única unidade.  
  
- Exibir um único arquivo como uma hierarquia de subitens.  
  
- Exiba um contexto de comando em volta de editores.  
  
- Exibir um contexto de serviço para editores.  
  
## <a name="use-an-existing-project-type"></a>Usar um tipo de projeto existente  
 Às vezes, a criação de um novo projeto não é necessária. A tabela a seguir mostra as tarefas para as quais você não precisa criar um tipo de projeto.  
  
|Tarefa|Descrição|  
|----------|-----------------|  
|Manipulando comandos|Qualquer VSPackage pode manipular comandos.|  
|Criando um editor|Editores personalizados podem ser registrados. Para obter mais informações, consulte [janelas de documentos e editores](https://msdn.microsoft.com/603625e1-62b6-413a-bc44-089346e166bc).|  
|Janelas proprietárias|Você pode criar as janelas de ferramentas e de documentos sem adicionar um novo tipo de projeto.|  
|Expondo Propriedades no janela Propriedades|Todos os objetos podem expor propriedades.|  
  
## <a name="create-a-project-subtype"></a>Criar um subtipo de projeto  
 Você pode usar subtipos de projeto para estender um tipo de projeto gerenciado sem precisar criar um novo tipo de projeto. Os subtipos de projeto usam agregação COM para estender projetos gerenciados escritos na Microsoft [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] ou [!INCLUDE[csprcs](../../includes/csprcs-md.md)] . Com a agregação COM, você pode reutilizar grande parte da implementação do sistema de projeto gerenciado e ainda Personalizar para um cenário específico por meio da agregação e do uso de interfaces de suporte. Para obter mais informações sobre subtipos de projeto, consulte [subtipos de projeto](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Consulte Também  
 [Documentar janelas e editores](https://msdn.microsoft.com/603625e1-62b6-413a-bc44-089346e166bc)   
 [Lista de verificação: criando novos tipos de projeto](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Hierarquias no Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
