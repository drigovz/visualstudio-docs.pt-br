---
title: 'Área de Teste 7: Compartilhar | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], sharing items
- source control plug-ins, sharing items
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd4c48e94015d95f5e56d465cdbf98562108d3b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704399"
---
# <a name="test-area-7-share"></a>Testar área 7: compartilhar
Esta área de teste abrange o compartilhamento de itens entre locais através do comando **Compartilhar.**

 Uma operação de lebre é a aparente duplicação de arquivos e itens de pasta entre dois ou mais locais dentro de uma hierarquia de arquivo de controle de origem. A duplicação realmente não ocorre no servidor, mas o usuário vê o mesmo arquivo em dois ou mais locais especificados. Sempre que são feitas alterações em qualquer um dos itens compartilhados, essas alterações aparecem em todos os outros locais compartilhados.

 O compartilhamento em pastas funciona se você selecionar uma pasta com pelo menos um arquivo sob controle de origem nele. O comando share está desativado nas seguintes condições:

- Se a pasta selecionada for uma pasta vazia.

- Se houver uma pasta real, mas não contiver arquivos de controle de origem.

- Se houver uma pasta virtual, se os arquivos sob controle de origem estão nela ou não.

- Se houver um projeto da Web do Site Remoto.

## <a name="command-menu-access"></a>Acesso ao menu de comando
 Os [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] seguintes caminhos do menu do ambiente de desenvolvimento integrado são usados nos casos de teste.

 Compartilhar: **Compartilhamento de**->controle**de**->origem**de arquivo**.

## <a name="expected-behavior"></a>Comportamento esperado

- O arquivo compartilhado aparece no local compartilhado.

- A visualização do histórico da versão de controle de origem mostra que os arquivos(s) são compartilhados.

- A edição de um arquivo compartilhado edita ambos os locais do arquivo.

## <a name="test-cases"></a>Casos de teste
 A seguir, casos específicos de teste para a área de teste Share.

|Ação|Etapas de teste|Resultados esperados para verificar|
|------------|----------------|--------------------------------|
|Compartilhe um arquivo de um projeto carregado sob controle de origem para outro projeto carregado|1. Crie um novo projeto.<br />2. Adicione um segundo projeto à solução.<br />3. Crie um arquivo no segundo projeto com um nome que não esteja no primeiro projeto.<br />4. Adicione a solução ao controle de origem.<br />5. Selecione o primeiro projeto.<br />6. Abra a caixa de diálogo **Compartilhar** **(Compartilhamento de** -> **Controle de Origem** -> **de Arquivo).**<br />7. Compartilhe o arquivo do segundo projeto para o primeiro projeto.<br />8. Aceite **verificar se** solicitado.|Comportamento Esperado Comum.|
|Compartilhe um arquivo de um projeto para outro|1. Crie um novo projeto.<br />2. Adicione-o ao controle de origem.<br />3. Feche a solução.<br />4. Crie um segundo projeto (nova solução.)<br />5. Adicione a solução ao controle de origem.<br />6. Selecione o projeto.<br />7. Abra a caixa **de** diálogo Compartilhar **(File** -> **Source Control** -> **Share).**<br />8. Compartilhe um arquivo do projeto anteriormente adicionado ao projeto aberto.<br />9. Aceite **verificar se** solicitado.|Comportamento Esperado Comum.|
|Compartilhe um arquivo que não faz parte do projeto do controle de origem no projeto carregado no momento|1. Crie um novo projeto.<br />2. Adicione a solução ao controle de origem.<br />3. Adicione um arquivo ao controle de origem que não faça parte do projeto ou da solução.<br />4. Selecione o projeto e abra a caixa **de** diálogo Compartilhar **(File** -> **Source Control** -> **Share).**<br />5. Selecione um arquivo na caixa de diálogo **Compartilhar** que não existe dentro do projeto ou solução atual e compartilhá-lo.<br />6. Aceite **verificar se** solicitado.|A loja de controle de origem realizou um Get, então o arquivo está agora no local local do projeto.|
|Compartilhar arquivos dentro do mesmo projeto para uma pasta diferente|1. Selecione **Verificar automaticamente** no Controle**de Origem de Opções** -> **Source Control** **de Ferramentas** -> .<br />2. Crie um novo projeto e adicione-o ao controle de origem.<br />3. Adicione uma pasta ao projeto.<br />4. Adicione um arquivo à pasta e verifique na pasta.<br />5. Selecione a pasta.<br />6. Abra a caixa de diálogo **Compartilhar** **(Compartilhamento de** -> **Controle de Origem** -> **de Arquivo).**<br />7. Compartilhe o arquivo com a pasta selecionada.|Comportamento Esperado Comum.<br /><br /> A pasta deve ser verificada com um arquivo nele antes de ser usada para compartilhamento.|
|Compartilhe uma pasta no Projeto carregado — Recursivo|1. Crie um novo projeto.<br />2. Adicione a solução ao controle de origem.<br />3. Selecione o projeto.<br />4. Abra a caixa **de** diálogo Compartilhar **(File** -> **Source Control** -> **Share).**<br />5. Selecione uma pasta.<br />6. Compartilhe a pasta recursivamente no projeto.|Comportamento Esperado Comum.|
|Compartilhe vários arquivos de um projeto para outro|1. Crie um novo projeto com vários arquivos nele.<br />2. Adicione a solução ao controle de origem.<br />3. Feche a solução.<br />4. Crie um novo projeto em uma nova solução.<br />5. Adicione a solução ao controle de origem.<br />6. Selecione o projeto.<br />7. Abra a caixa **de** diálogo Compartilhar **(File** -> **Source Control** -> **Share).**<br />8. Compartilhe vários arquivos do projeto criado anteriormente para o projeto atualmente aberto.|Comportamento Esperado Comum.|

## <a name="see-also"></a>Confira também
- [Guia de teste para plug-ins de controle do código-fonte](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
