---
title: 'Área de Teste 3: Confira o Checkout | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, checkout
- source control plug-ins, undo checkout
- source control [Visual Studio SDK], checking out
- source control [Visual Studio SDK], undo checkout
ms.assetid: ce00c5a5-d472-4f45-8776-d77a1fbe9d37
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5365da1e342df5aea9c1b1cd2ae5a446baea57f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704612"
---
# <a name="test-area-3-check-outundo-checkout"></a>Área de teste 3: Check Out/Undo Checkout
Esta área de teste plug-in de controle de origem abrange a edição e a reversão de itens da loja de versões através dos comandos **Check Out** e **Desfazer Checkout.**

**Confira**: Marca um item na loja de versões como verificado, modifica a cópia local para ler/escrever.

**Desfazer checkout**: Marca um item na loja de versões como check-in, reverte a cópia local para o estado antes do check-out (dependendo das opções).

## <a name="command-menu-access"></a>Acesso ao menu de comando

Os [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] seguintes caminhos do menu do ambiente de desenvolvimento integrado são usados nos casos de teste.

##### <a name="check-out"></a>Check-out:

- **Arquivo,** **Controle de Origem,** **Check Out**.

- **Arquivo**, **Check Out**.

- Menu de atalho, **check-out**.

- Desfazer checkout: **Arquivo,** **Controle de Origem,** **Desfazer Checkout**.

## <a name="common-expected-behavior"></a>Comportamento Esperado Comum

- Após a operação de check-out, os arquivos de destino e/ou pastas são marcados como verificados na loja de versões.

- A loja de versões atribui o checkout ao usuário correto.

- A hora e a data do checkout estão corretas (de acordo com as configurações do usuário).

## <a name="test-cases"></a>Casos de teste

A seguir, casos específicos de teste para a área de teste Checkout/Undo Checkout.

### <a name="case-3a-check-out"></a>Caso 3A: Confira

Esta seção se concentra na operação do comando check-out.

|Ação|Etapas de teste|Resultados esperados para verificar|
|------------|----------------|--------------------------------|
|Confira um projeto de cliente exclusivo (COE)|1. Crie um projeto cliente.<br />2. Adicione a solução ao controle de origem.<br />3. Confira o projeto inteiro com exclusividade **(Arquivo**, **Check Out**).|O check-out ocorre.|
|Confira exclusivo (COE) um sistema de arquivos ou projeto Web IIS local|1. Defina a conexão do servidor web para compartilhar arquivos em **ferramentas,** **opções,** **projetos,** **configurações da Web**.<br />2. Crie um projeto Web.<br />3. Adicione a solução ao controle de origem.<br />4. Confira o projeto inteiro com exclusividade **(Arquivo,** **Controle de Origem,** **Check Out**).|O check-out ocorre.|
|Confira os itens da solução em uma solução (novo método para lidar com outros arquivos)|1. Crie uma solução em branco.<br />2. Adicione a solução ao controle de origem.<br />3. Verifique a solução.<br />4. Adicione vários itens de solução.<br />5. Verifique todos os itens recém-adicionados.<br />6. Selecione vários itens de solução.<br />7. Confira os itens selecionados (Menu atalho, **Check Out**).|Os arquivos selecionados são verificados.|
|Confira a versão local (se o plug-in em teste suporta esse recurso)|1. Usuário 1: Crie um projeto cliente.<br />2. Usuário 1: Adicione a solução ao controle de origem.<br />3. Usuário 2: Abra a solução do controle de origem para outro local.<br />4. Usuário 2: Confira um arquivo.<br />5. Usuário 2: Modifique o arquivo.<br />6. Usuário 2: Verifique no arquivo.<br />7. Usuário 1: Confira a versão local do arquivo (Confira a opção avançada **Check Out Versão Local** na caixa de diálogo Check **Out).**|A versão local do arquivo é verificada.<br /><br /> As modificações do usuário 2 não são aplicadas ao arquivo do Usuário 1.|

### <a name="case-3b-disconnected-check-out"></a>Caso 3b: Desconectado Check out

Operar no modo desconectado permite aos usuários algum nível de suporte contínuo ao controle de origem quando não conectado diretamente a um armazenamento de versões. Isso é feito por cache local de todas as informações relevantes sobre a solução e projetos alistados.

Operações exclusivas de check-out só podem ocorrer quando conectadas ao armazenamento de controle de origem. Operações de check-out compartilhadas podem ocorrer a qualquer momento, seja conectado ou desconectado. Portanto, quando desconectado da loja de versões, apenas o comando **Check Out Shared** (COS) está habilitado. Enquanto estiver desconectado, **o Desfazer checkout** está desativado porque a versão antiga não pode ser recuperada para substituir as alterações feitas pelo usuário.

Quando o usuário se reconecta à loja de versões, os estados de checkout de todas as soluções e projetos alistados são sincronizados. Isso faz as atualizações necessárias à loja para os checkouts que o usuário realizou. Uma vez que a sincronização tenha acontecido, o usuário pode continuar trabalhando normalmente (conectado).

#### <a name="expected-behavior"></a>Comportamento esperado

- Não é possível usar o comando **Check Out Exclusivamente** enquanto estiver desconectado da loja de versões.

- Não é possível usar o comando **Desfazer checkout** enquanto estiver desconectado do armazenamento de versões.

- **O** comando Check Out compartilhado funciona.

|Ação|Etapas de teste|Resultados esperados para verificar|
|------------|----------------|--------------------------------|
|Enquanto estiver desconectado, verifique um arquivo e conecte-se para sincronização|1. Desconecte um projeto controlado usando a caixa de diálogo Controle de alteração de origem **(Arquivo,** **Controle de origem,** **controle de origem de alteração).**<br />2. Verifique um arquivo.<br />3. Clique em Sair (desconectado) na caixa de diálogo de aviso.<br />4. Editar o arquivo.<br />5. Conecte-se usando a caixa de diálogo Controle de alteração de origem.<br />6. Obtenha a versão mais recente do arquivo editado.|Comportamento Esperado Comum|

### <a name="case-3c-query-editquery-save-qeqs"></a>Caso 3c: Consulta Edit/Query Save (QEQS)
 Os itens sob controle de origem são rastreados para edições, alterações e salvamentos para ajudar os usuários a gerenciar facilmente seus arquivos. Quando um item controlado que é "check-in" é editado, o QEQS intercepta a tentativa de edição e pergunta ao usuário se ele quer verificar o arquivo para editá-lo. Dependendo das **configurações de Ferramentas**, **Opções,** o usuário é forçado a verificar o arquivo para editar ou pode ser autorizado a editar uma cópia na memória e sair mais tarde. Se a configuração **Ferramentas**, **Opções** do usuário não estiver definida para exibir a caixa de diálogo de check-out e apenas para verificar, então, à medida que o usuário faz sua edição, o arquivo é automaticamente verificado, sempre que possível.

#### <a name="expected-behavior"></a>Comportamento esperado

- Após a operação de check-out, os arquivos de destino e/ou pastas são marcados como verificados na loja de versões.

- A loja de versões atribui o check-out ao usuário correto.

- A hora e a data do check-out estão corretas (de acordo com as configurações do usuário).

- A cópia local do arquivo ou pasta de destino é gravável.

|Ação|Etapas de teste|Resultados esperados para verificar|
|------------|----------------|--------------------------------|
|Editar arquivo de texto que é verificado em|1. Crie um novo projeto contendo um arquivo de texto.<br />2. Adicione a solução ao controle de origem.<br />3. Defina **ferramentas,** **opções,** **controle de origem,** **permita que os arquivos sejam editados enquanto somente leitura em disco** para sem verificação.<br />4. Defina **ferramentas,** **opções,** **controle de origem,** **prompt para check-out** na caixa de combo **de verificação quando verificada são editadas.**<br />5. Defina **ferramentas,** **opções,** **controle de origem,** **prompt para check-out** na caixa de combinação **quando verificada são salvas.**<br />6. Abra o arquivo de texto no editor, tente digitar um novo texto no arquivo. Se esse passo for bem sucedido, continue até o próximo passo.<br />7. Clique em **Cancelar** na **caixa de diálogo 'Editar'.** Se esse passo for bem sucedido, continue até o próximo passo.<br />8. Defina **ferramentas,** **opções,** **controle de origem,** **permita que os arquivos sejam editados durante** a leitura somente no disco para verificação.<br />9. Abra o arquivo do projeto no editor, tente digitar um novo texto no arquivo. Se esse passo for bem sucedido, continue até o próximo passo.<br />10. Clique em **Editar** na caixa de diálogo **'Editar'.** Se esse passo for bem sucedido, continue até o próximo passo.<br />11. Edite o arquivo de texto e tente salvá-lo.|`Result of step 6:`<br /><br /> Confira a caixa de diálogo Editar é exibida.<br /><br /> `Result of step 7:`<br /><br /> O arquivo está inalterado.<br /><br /> `Result of step 9:`<br /><br /> Confira a caixa de diálogo Editar é exibida.<br /><br /> `Result of step 10:`<br /><br /> Você pode editar o arquivo do projeto na memória.<br /><br /> `Result of step 11:`<br /><br /> Ao salvar, a caixa de diálogo 'Salvar' é exibida.|
|Editar um arquivo de solução que é verificado|Repita as etapas descritas no teste anterior, mas em vez de modificar um arquivo de texto, modifique a solução alterando as propriedades da solução.|O mesmo que o teste anterior|
|Editar um arquivo de projeto que é verificado|Repita as etapas descritas no teste anterior, mas em vez de modificar um arquivo de texto, modifique o projeto alterando as propriedades do projeto.|O mesmo que o teste anterior.|

### <a name="case-3d-silent-check-out"></a>Caso 3d: Check Out silencioso
 Esta subárea abrange os cenários em que a caixa de diálogo **Check Out** não aparece por parte das **configurações ferramentas,** **opções,** controle de origem do **usuário.**

#### <a name="expected-behavior"></a>Comportamento esperado

- Após a operação de check-out, os arquivos de destino e/ou pastas são marcados como verificados na loja de versões.

- A loja de versões atribui o check-out ao usuário correto.

- A hora e a data do check-out estão corretas (de acordo com as configurações do usuário).

- A cópia local do arquivo ou pasta de destino é gravável.

|Ação|Etapas de teste|Resultados esperados para verificar|
|------------|----------------|--------------------------------|
|Check-out silencioso para um arquivo|1. Defina **ferramentas,** **opções,** **controle de origem** para arquivos de **checkout automaticamente na edição**.<br />2. Crie um novo projeto com um arquivo.<br />3. Adicione a solução ao controle de origem.<br />4. Verifique o arquivo.|O arquivo é verificado silenciosamente (sem ui).|
|Checkout silencioso para um projeto|1. Defina **ferramentas,** **opções,** **controle de origem** para arquivos de **checkout automaticamente na edição**.<br />2. Crie um novo projeto.<br />3. Adicione a solução ao controle de origem.<br />4. Confira o projeto.|O arquivo é verificado silenciosamente (sem ui).|

### <a name="case-3e-undo-check-out"></a>Caso 3e: Desfazer check-out
 **Desfazer check-out** é usado para cancelar o status de check-out de um arquivo e evitar verificar as alterações feitas no arquivo.

#### <a name="expected-behavior"></a>Comportamento esperado

- O padrão é baseado na configuração **"Check out Local Version"** do usuário. Se o usuário optou por verificar a versão local, então o padrão para desfazer o check-out é sempre reverter para a versão verificada.

- Após a aceitação do desfazer, os ícones **do Solution Explorer** são atualizados para arquivos afetados e o item é removido da janela **Checkins pendentes.**

|Ação|Etapas de teste|Resultados esperados para verificar|
|------------|----------------|--------------------------------|
|Desfazer checkout de um único arquivo que é verificado exclusivamente|1. Crie um projeto cliente.<br />2. Adicione a solução ao controle de origem.<br />3. Confira um arquivo exclusivamente.<br />4. Modifique o arquivo.<br />5. Desfazer checkout **(arquivo,** **controle de origem,** **desfazer checkout**).|Comportamento Esperado Comum.|
|Desfazer checkout de um único arquivo que é verificado Compartilhado|1. Crie um projeto cliente.<br />2. Adicione a solução ao controle de origem.<br />3. Confira um arquivo compartilhado.<br />4. Modifique o arquivo.<br />5. Desfazer checkout **(arquivo,** **controle de origem,** **desfazer checkout**).|Comportamento Esperado Comum.|
|Desfazer o check-out de um projeto após adicionar arquivos ao projeto|1. Crie um novo projeto e adicione-o ao controle de origem.<br />2. Confira o projeto.<br />3. Adicione um arquivo ao projeto.<br />4. Desfaça checkout do projeto.|O arquivo adicionado é removido do projeto no Solution Explorer.<br /><br /> O projeto não está mais descontrolado.|
|Desfazer o check-out de um projeto após a exclusão de arquivos do projeto|1. Crie um novo projeto e adicione-o ao controle de origem.<br />2. Confira o projeto.<br />3. Exclua um arquivo do projeto.<br />4. Desfaça checkout do projeto.|O arquivo excluído aparece sob o projeto no Solution Explorer.<br /><br /> O projeto não está mais descontrolado.|

## <a name="see-also"></a>Confira também
- [Guia de teste para plug-ins de controle do código-fonte](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
