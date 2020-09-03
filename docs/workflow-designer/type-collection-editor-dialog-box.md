---
title: Caixa de diálogo Editor de coleção de tipo Designer de Fluxo de Trabalho
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TypeCollectionEditor.UI
ms.assetid: 63cdea6b-bca2-4c06-b8b4-c8faabd40726
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 023d049c5256abe6212dd65df78cd67151be94a2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75593051"
---
# <a name="type-collection-editor-dialog-box"></a>Digite a caixa de diálogo Editor de Coleção

A caixa de diálogo **Editor de coleção de tipos** é usada para adicionar tipos conhecidos às atividades **Enviar** e **receber** . Essa caixa de diálogo também é usada para adicionar argumentos de tipo genérico à atividade **InvokeMethod** . Quando usado para as atividades **Enviar** e **receber** para adicionar tipos conhecidos, a caixa de diálogo Editor de **coleção de tipos** exige que as adições de tipo sejam exclusivas. Se um tipo duplicado for adicionado e a alteração for confirmada clicando em **OK**, uma mensagem de erro será retornada. Quando usado para a atividade **InvokeMethod** adicionar argumentos de tipo genérico, a caixa de diálogo **Editor de coleção de tipos** permite a adição de tipos duplicados.

Para obter mais informações, consulte [tipos conhecidos de contrato de dados](/dotnet/framework/wcf/feature-details/data-contract-known-types).

A tabela a seguir descreve os elementos da interface do usuário da caixa de diálogo de **coleção de tipos** .

|Elemento da interface do usuário|Descrição|
|-|-----------------|
|**Lista de Tipos**|Uma lista de tipos que foram adicionados ou removidos.|

## <a name="to-bring-up-the-type-collection-editor-for-the-send-and-receive-activities"></a>Para transferir anterior o Editor de Coleção do tipo para o enviar e receber atividades

1. Selecione a atividade **Enviar** ou **receber** no modo de exibição de design.

2. Pressione **F4** para exibir a janela **Propriedades** .

3. Na janela **Propriedades** , clique no botão de reticências ao lado da propriedade **KnownTypes** .

## <a name="to-bring-up-the-type-collection-editor-for-the-invokemethod-activity"></a>Para transferir anterior o Editor de Coleção do tipo para atividades de InvokeMethod

1. Selecione a atividade **InvokeMethod** no modo de exibição de design.

2. Pressione **F4** para exibir a janela **Propriedades** .

3. Na janela **Propriedades** , clique no botão de reticências ao lado da propriedade **genericTypeArguments** .
