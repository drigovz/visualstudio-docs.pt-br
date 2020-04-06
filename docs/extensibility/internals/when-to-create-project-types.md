---
title: Quando criar tipos de projetos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 861250dac25288f353cbd5c57f510bf67dadce70
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703424"
---
# <a name="when-to-create-project-types"></a>Quando criar tipos de projeto
A criação de um novo tipo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de projeto fornece uma base para personalização para seus usuários. No entanto, a criação de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] um novo tipo de projeto não é necessária para todas as personalizações. As seguintes diretrizes devem ajudá-lo a determinar se um novo tipo de projeto é necessário para o seu cenário.

## <a name="create-a-new-project-type"></a>Criar um novo tipo de projeto
 Você deve criar um tipo de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projeto se quiser personalizar para agir de uma ou mais das seguintes maneiras:

- Participe da compilação, implantação, configurações e controle de origem.

- Ofereça suporte à depuração.

- Exibir itens do projeto no **Solution Explorer**.

- Use a caixa de diálogo **Projeto Aberto** ou **Novo Projeto.**

- Apoie o projeto de aninhamento.

## <a name="extend-an-existing-project-type"></a>Estender um tipo de projeto existente
 Você pode querer criar um novo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tipo de projeto que possa ser usado das seguintes maneiras para modificar [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] ou estender o comportamento de um tipo de projeto existente, por exemplo, modificando o processo de construção de projetos:

- Trabalhe com vários arquivos como uma única unidade.

- Exibir um único arquivo como uma hierarquia de subitens.

- Exibir um contexto de comando em torno de editores.

- Exibir um contexto de serviço para editores.

## <a name="use-an-existing-project-type"></a>Use um tipo de projeto existente
 Criar um novo projeto às vezes não é necessário. A tabela a seguir mostra as tarefas para as quais você não precisa criar um tipo de projeto.

|Tarefa|Descrição|
|----------|-----------------|
|Comandos de manuseio|Qualquer VSPackage pode lidar com comandos.|
|Construindo um editor|Editores personalizados podem ser registrados. Para obter mais informações, consulte [Document Windows e Editores](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc).|
|Possuir janelas|Você pode criar janelas de ferramentas e documentos sem adicionar um novo tipo de projeto.|
|Expondo propriedades na janela Propriedades|Todos os objetos podem expor propriedades.|

## <a name="create-a-project-subtype"></a>Criar um subtipo de projeto
 Você pode usar subtipos de projeto para estender um tipo de projeto gerenciado sem ter que criar um novo tipo de projeto. Os subtipos do projeto usam a agregação [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] COM [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]para estender projetos gerenciados escritos na Microsoft ou . Com a agregação COM, você pode reutilizar grande parte da implementação gerenciada do sistema de projetos e ainda personalizar para um cenário específico através da agregação e do uso de interfaces de suporte. Para obter mais informações sobre subtipos de projeto, consulte [Subtipos do Projeto](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Confira também
- [Documentos Windows e Editores](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc)
- [Lista de verificação: criando novos tipos de projeto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Hierarquias no Visual Studio](../../extensibility/internals/hierarchies-in-visual-studio.md)
