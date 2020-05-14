---
title: 'Área de teste 4: check-in | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], checking items in
- source control plug-ins, checking items in
ms.assetid: d0329fa8-7a8d-4d30-b67b-6f2a97b75a30
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2386a217de228c5c47b467e6e083d978702927f4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704570"
---
# <a name="test-area-4-check-in"></a>Área de teste 4: fazer check-in
Esta área de teste plug-in de controle de origem abrange o envio de itens atualizados para a loja de versões através do comando **Check In.**

## <a name="command-menu-access"></a>Acesso ao menu de comando
 Os [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] seguintes caminhos do menu do ambiente de desenvolvimento integrado são usados nos casos de teste.

##### <a name="check-in"></a>Check-in:
 **Arquivo,** **controle de origem,** **check-in**.

 **Arquivo,** **Check-In**.

 Menu de atalho, **Check In**.

## <a name="common-expected-behavior"></a>Comportamento Esperado Comum

- Projetos e arquivos adicionados a uma solução ou projeto sob controle de origem aparecem na caixa de diálogo **'Check In'** e na janela **Checkins pendentes.**

- Após o check-in, itens adicionados aparecem no controle de origem.

- Após o check-in, os itens atualizados são devidamente versões na loja.

## <a name="test-cases"></a>Casos de teste
 A seguir, casos específicos de teste para a área de teste de Checkin.

### <a name="case-4a-modified-items"></a>Caso 4a: Itens modificados
 Descreve o uso da ação de check-in para atualizar um arquivo sob controle de origem que foi modificado.

|Ação|Etapas de teste|Resultados esperados para verificar|
|------------|----------------|--------------------------------|
|Modifique um arquivo de texto que tenha sido verificado, verifique apenas em arquivo (Caixa de diálogo**Check In)**|1. Crie um novo projeto com um arquivo de texto.<br />2. Adicione a solução ao controle de origem.<br />3. Confira e modifique o arquivo de texto.<br />4. Faça check-in através da caixa de diálogo Check In **(Arquivo,** **Controle de Origem,** **Entrada).**|Comportamento Esperado Comum.|
|Modifique um arquivo de texto que tenha sido verificado, Verifique somente em arquivo (janela**Checkins pendentes)**|1. Crie um novo projeto com um arquivo de texto.<br />2. Adicione a solução ao controle de origem.<br />3. Confira e modifique o arquivo de texto.<br />4. Faça o check-in através da janela **Checkins pendentes.**|Comportamento Esperado Comum.|

### <a name="case-4b-adding-files"></a>Caso 4b: Adicionando arquivos
 Ao adicionar um arquivo a um projeto ou um item a uma solução, o projeto ou solução também deve mudar. Assim, o arquivo pai também é verificado e deve ser verificado para completar a adição.

|Ação|Etapas de teste|Resultados esperados para verificar|
|------------|----------------|--------------------------------|
|Adicione um arquivo de texto e faça check-in em tudo (Caixa de diálogo**Check In)**|1. Crie um novo projeto.<br />2. Adicione a solução ao controle de origem.<br />3. Adicione um arquivo de texto ao projeto.<br />4. Aceite sair do projeto se solicitado.<br />5. Selecione a solução no **Solution Explorer**.<br />6. Faça o check-in na caixa de diálogo **"Entrada in".**|Comportamento Esperado Comum.|
|Adicione um arquivo de texto e verifique em tudo (janela**Checkins pendentes)**|1. Crie um novo projeto.<br />2. Adicione a solução ao controle de origem.<br />3. Adicione um arquivo de texto ao projeto.<br />4. Aceite sair do projeto se solicitado.<br />5. Verifique a solução da janela **Checkins pendentes.**|Comportamento Esperado Comum|

### <a name="case-4c-adding-projects"></a>Caso 4c: Adicionando projetos
 Ao adicionar um projeto a uma solução, a solução também deve mudar. Assim, o arquivo de solução também é verificado e deve ser verificado para completar a adição.

|Ação|Etapas de teste|Resultados esperados para verificar|
|------------|----------------|--------------------------------|
|Adicione um projeto a uma solução em branco sob controle de origem (Caixa de diálogo **'Entrada'**|1. Crie uma solução em branco.<br />2. Adicione a solução ao controle de origem.<br />3. Adicione um novo projeto.<br />4. Aceite sair da solução se solicitado.<br />5. Faça o check-in na caixa de diálogo **"Entrada in".**|Comportamento Esperado Comum.|
|Adicione um projeto a uma solução em branco sob controle de origem (janela**Checkins pendentes)**|1. Crie uma solução em branco.<br />2. Adicione a solução ao controle de origem.<br />3. Adicione um novo projeto.<br />4. Aceite sair da solução se solicitado.<br />5. Verifique a solução da janela **Checkins pendentes.**|Comportamento Esperado Comum.|

## <a name="see-also"></a>Confira também
- [Guia de teste para plug-ins de controle do código-fonte](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
