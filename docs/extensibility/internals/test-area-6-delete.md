---
title: 'Área de Teste 6: Exclua | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], deleting items
- source control plug-ins, deleting items
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9902ab9d1cb9c28ddf67b83590a4cccd5f6562f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704505"
---
# <a name="test-area-6-delete"></a>Área de teste 6: excluir
Esta área de teste plug-in de controle de origem abrange ações de exclusão.

 O controle de origem responde à exclusão de ações no **Solution Explorer**.

 A seguir está uma lista de itens que podem ser excluídos:

- Arquivos

- Pastas

- Project

  Dependendo do tipo de projeto, você pode ter a opção **de Remover** o projeto (deixa os arquivos no disco) ou **Excluir** o projeto (remove os arquivos no disco). Qualquer ação remove o projeto ou item do **Solution Explorer**.

## <a name="expected-behavior"></a>Comportamento esperado
 O comportamento esperado para os casos de teste na área de teste de exclusão é:

- O item excluído não é mais visível dentro **do Solution Explorer**.

- O pai do projeto ou item excluído é verificado conforme necessário (possivelmente com um prompt.)

- Depois de excluir um item de check-out ou adicionado, ele NÃO aparece na janela **Checkins pendentes.**

- O item ainda existe dentro do armazenamento de controle de origem, mesmo após a exclusão, e deve ser eliminado manualmente.

|Ação|Etapas de teste|Resultados esperados para verificar|
|------------|----------------|--------------------------------|
|Exclua um projeto cliente|1. Crie um projeto cliente.<br />2. Adicione a solução ao controle de origem.<br />3. Remova todo o projeto da solução|Comportamento Esperado Comum.|
|Exclua um arquivo vazio|1. Crie um projeto cliente.<br />2. Adicione um arquivo de byte zero ao projeto.<br />3. Adicione a solução ao controle de origem.<br />4. Selecione o arquivo, exclua-o.|Comportamento Esperado Comum.|
|Exclua uma pasta com um arquivo|1. Crie uma solução de projeto único.<br />2. Adicione uma pasta.<br />3. Adicione um arquivo à pasta.<br />4. Adicione a solução ao controle de origem.<br />5. Confira o projeto para evitar solicitações.<br />6. Exclua a pasta.|Comportamento Esperado Comum.|
|Exclua um projeto web do sistema de arquivos|1. Crie um projeto Web do sistema de arquivos (use o botão Procurar para especificar um caminho UNC).<br />2. Adicione a solução ao controle de origem.<br />3. Remova todo o projeto da solução.<br />4. Repita as etapas 1 a 3 para um projeto web local (exercita caminhos diferentes através do código, mas tem a mesma interface e comportamento externo).|Comportamento Esperado Comum.|
|Exclua um arquivo de um projeto web do sistema de arquivos|1. Crie um projeto Web do sistema de arquivos.<br />2. Adicione a solução ao controle de origem.<br />3. Exclua um arquivo do projeto.<br />4. Repita as etapas 1 a 3 para um projeto web local (exercita caminhos diferentes através do código, mas tem a mesma interface e comportamento externo).|Comportamento Esperado Comum.|

## <a name="see-also"></a>Confira também
- [Guia de teste para plug-ins de controle do código-fonte](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
