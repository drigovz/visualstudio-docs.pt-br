---
title: 'Área de Teste 5: Controle de Fonte de Mudança | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], changing
- source control plug-ins, changing source control
ms.assetid: fdf09e00-108c-4d51-bbd5-72452d52a490
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d1c0df31fbecd532e6a5f7f317730cd995cd8225
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704519"
---
# <a name="test-area-5-change-source-control"></a>Área de teste 5: alterar o controle do código-fonte
Esta área de teste plug-in de controle de origem abrange a alteração do controle de origem através do comando **Change Source Control.**

 **O** comando Change Source Control fornece quatro funções básicas para o usuário:

- **Ligar:**

   Permite que um usuário estabeleça ou restabeleça um link de controle de origem entre uma solução/projeto e o armazenamento de versões.

- **Desvincular:**

   Remove um projeto/solução do controle de origem em uma base por conexão.

- **Conectar/desconectar:**

  Alternações de estado conectado ou off-line da solução controlada, que está coberta na Área 3. Para obter mais informações, consulte [área de teste 3: Check Out/Undo Checkout](../../extensibility/internals/test-area-3-check-out-undo-checkout.md).

## <a name="command-menu-access"></a>Acesso ao menu de comando
 O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] seguinte caminho de menu do ambiente de desenvolvimento integrado é usado nos casos de teste.

 Controle de origem de alteração:**arquivo,** **controle de origem,** **controle de origem de alteração**.

## <a name="test-cases"></a>Casos de teste
 A seguir, casos de teste específicos para a área de teste de comando **Change Source Control.**

### <a name="case-5a-bind"></a>Caso 5a: Vincular
 O Bind permite que o usuário adicione informações de controle de código-fonte aos projetos e soluções selecionados. O usuário é normalmente solicitado a identificar um projeto no controle de origem ao qual estes devem ser adicionados. O usuário pode não criar um novo projeto no controle de origem como parte desta operação (contraste com Adicionar ao Controle de Origem).

| Ação | Etapas de teste | Resultados esperados para verificar |
| - | - | - |
| Vincule-se ao local vazio | 1. Crie um projeto.<br />2. Adicione a solução ao controle de origem.<br />3. Caixa de diálogo Controle **de código de** mudança aberta **(arquivo,** **controle de origem,** **controle de fonte de alteração).**<br />4. Clique em **Desvincular**.<br />5. Aceite a caixa de diálogo de aviso se ela aparecer.<br />6. Selecione todos os itens.<br />7. Clique **em Ligar**.<br />8. Navegue até um local vazio em uma loja de controle de origem.<br />9. Clique em **OK** para fechar a caixa de diálogo **Alterar controle de** origem.<br />10. Clique em **Continuar com essas amarras** na caixa de diálogo de confirmação.<br />11. Clique em **OK** na caixa de diálogo de aviso se ela aparecer.<br />12. Verifique tudo. Se esse passo for bem sucedido, continue até o próximo passo.<br />13. Abra a solução do controle de origem para um novo local. | `Result from Step 12:`<br /><br /> Solução e projeto são vinculados e escritos para o novo alvo na loja de versões.<br /><br /> Os arquivos de solução e projeto são verificados.<br /><br /> A hierarquia do projeto da loja de versão corresponde à hierarquia da pasta do projeto em disco.<br /><br /> `Result from Step 13:`<br /><br /> Todos os itens do projeto são baixados. |
| Vincule-se ao local que está em sincronia com o cliente | 1. Crie um projeto.<br />2. Adicione a solução ao controle de origem.<br />3. Crie uma duplicata da solução e projete [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]na loja de versões (Compartilhar e Ramo se estiver usando ).<br />4. Caixa de diálogo Controle **de código de** mudança aberta **(arquivo,** **controle de origem,** **controle de fonte de alteração).**<br />5. Desvincular tudo.<br />6. Clique em **OK** para fechar a caixa de diálogo **Alterar controle** de origem.<br />7. Reabrir a caixa de diálogo **Controle de origem** de alteração.<br />8. Selecione todos.<br />9. Clique **em Ligar**.<br />10. Navegue até o local ramificado da solução e do projeto (a partir da etapa 3)<br />11. Clique em **OK** para fechar a caixa de diálogo **Alterar controle de** origem.<br />12. Obtenha as últimas recursivamente para todos os itens. | O conteúdo do arquivo após o get é o mesmo de antes de começar. |
| Vincule-se ao local que está fora de sincronia com o cliente | 1. Crie um projeto.<br />2. Adicione a solução ao controle de origem.<br />3. Crie uma duplicata da solução e projete [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]na loja de versões (Compartilhar e Ramo se estiver usando ).<br />4. Modifique arquivos no projeto ramificado no armazenamento de versões.<br />5. Caixa de diálogo Controle **de código de** mudança aberta **(arquivo,** **controle de origem,** **controle de fonte de alteração).**<br />6. Desamarre tudo.<br />7. Clique em **OK** para fechar a caixa de diálogo **Alterar controle** de origem.<br />8. Reabrir a caixa de diálogo **Controle de origem** de alteração.<br />9. Selecione todos.<br />10. Clique **em Vincular**.<br />11. Navegue até o local ramificado para solução e projeto.<br />12. Clique em **OK** para fechar a caixa de diálogo **Alterar controle de** origem.<br />13. Aceitar caixa de diálogo Aviso se ela aparecer.<br />14. Obtenha o mais recente recursivo para todos os itens. | Os arquivos que foram modificados na Etapa 4 também são modificados localmente. |
| Solução de vinculação que nunca esteve sob controle de origem | 1. Crie uma pasta vazia no controle de origem.<br />2. Crie um projeto de cliente.<br />3. Caixa de diálogo Controle **de código de** mudança aberta **(arquivo,** **controle de origem,** **controle de fonte de alteração).**<br />4. Vincule a solução ao local vazio no controle de origem.<br />5. Clique em **OK** para fechar a caixa de diálogo **Alterar controle de** origem.<br />6. Clique em **Continuar com essas amarras** na caixa de diálogo de confirmação.<br />7. Clique em **OK** na caixa de diálogo de aviso se ela aparecer. | A solução é adicionada ao controle de origem.<br /><br /> Solução e projeto são verificados. |
| Cancelar vínculo | 1. Crie um projeto.<br />2. Adicione a solução ao controle de origem.<br />3. Abra a caixa de diálogo Controle de origem de alteração.<br />4. Desvincular tudo.<br />5. Clique no botão **OK** para fechar a caixa de diálogo. Se esse passo for bem sucedido, continue até o próximo passo.<br />6. Reabra a caixa de diálogo **Controle de origem** de alteração.<br />7. Vincule-se a um local não relacionado.<br />8. Clique **em Cancelar**. | `Result from Step 5:`<br /><br /> A solução não está mais sob controle de origem<br /><br /> `Result from Step 8:`<br /><br /> A solução ainda NÃO está sob controle de origem. |

### <a name="case-5b-unbind"></a>Caso 5b: Desvincular
 Desvincular remove informações de controle de código fonte de projetos e sua solução. Os projetos e a solução afetados são baseados em uma mistura de seleção de usuários e como os itens foram adicionados ao controle de origem.

|Ação|Etapas de teste|Resultados esperados para verificar|
|------------|----------------|--------------------------------|
|Desvincular solução contendo um sistema de arquivos ou projeto Web IIS local e um projeto cliente|1. Crie um sistema de arquivos ou um projeto web IIS local.<br />2. Adicione a solução ao controle de origem.<br />3. Adicione um novo projeto de cliente à solução.<br />4. Aceite verificar a solução se solicitado.<br />5. Abra a caixa de diálogo **Controle de origem** de alteração.<br />6. Clique em **Desvincular**.<br />7. Clique em **OK** para fechar a caixa de diálogo.<br />8. Tente verificar solução, projeto, itens de solução, itens do projeto.|Solução e projetos NÃO estão sob controle de origem.<br /><br /> Os comandos do menu controle de origem não aparecem.|
|Cancelar desvincular|1. Crie um projeto.<br />2. Adicione a solução ao controle de origem.<br />3. Abra a caixa de diálogo **Controle de origem** de alteração.<br />4. Clique em **Desvincular tudo**.<br />5. Clique **em Cancelar**.|A solução está sob controle de origem.|

### <a name="case-5c-rebind"></a>Caso 5c: Revinculação
 Rebind é simplesmente uma combinação de desvincular e vincular — o processo de revinculação de um projeto/solução que estava anteriormente sob controle de origem e foi desvinculado.

|Ação|Etapas de teste|Resultados esperados para verificar|
|------------|----------------|--------------------------------|
|Revincular solução e projetos sem fechar a caixa de diálogo **Controle de origem de** alteração|1. Crie um projeto.<br />2. Adicione a solução ao controle de origem.<br />3. Abra a caixa de diálogo **Controle de origem** de alteração.<br />4. Clique em **Desvincular**.<br />5. Selecione todas as linhas.<br />6. Clique **em Ligar**.<br />7. Clique em **OK** para fechar a caixa de diálogo **Alterar controle de** origem.<br />8. Aceite o checkout se solicitado.|Solução e projeto estão sob controle de origem.|
|Revincular o projeto somente sem fechar a caixa de diálogo **Alterar controle de origem**|1. Crie um projeto.<br />2. Adicione apenas o projeto ao controle de origem usando (>--fonte-controle->adicionar projetos selecionados ao controle de origem.<br />3. Abra a caixa de diálogo Controle de origem de alteração.<br />4. Desvincular apenas o projeto.<br />5. Vincular apenas o projeto.|A solução permanece descontrolada.<br /><br /> O projeto permanece controlado.|
|Revincular solução somente sem fechar a caixa de diálogo **Alterar controle de** fonte|1. Crie um projeto.<br />2. Adicione apenas a solução ao controle de origem usando **(Arquivo,** **Controle de Origem,** **Adicionar Projetos Selecionados ao Controle de Origem**.<br />3. Abra a caixa de diálogo **Controle de origem** de alteração.<br />4. Desvincular apenas a solução (Não feche a caixa de diálogo **Alterar controle** de origem.)<br />5. Amarre apenas a solução.<br />6. Clique em **OK** para fechar a caixa de diálogo.<br />7. Verifique os itens de solução e solução (se houver.)|A solução permanece controlada.<br /><br /> O projeto permanece descontrolado.|
|Revincular solução/projeto somente quando estiver no mesmo diretório|1. Crie um projeto.<br />2. Adicione apenas o projeto ao controle de origem usando **(Arquivo,** **Controle de Origem,** **Adicionar Projetos Selecionados ao Controle de Origem**.<br />3. Feche a solução.<br />4. Crie uma nova solução com pelo menos dois projetos.<br />5. Adicione a solução ao controle de origem.<br />6. Adicione o projeto criado na Etapa 1 a partir do controle de origem.<br />7. Aceite o check-out da solução se solicitado.<br />8. Verifique toda a solução.<br />9. Abra a caixa de diálogo **Controle de origem** de alteração.<br />10. Selecione o projeto adicionado (da Etapa 6) e clique **em Desvincular**.<br />11. Clique em **OK** para fechar a caixa de diálogo.<br />12. Aceite o checkout se solicitado.<br />13. Reabrir a caixa de diálogo **Controle de origem** de alteração.<br />14. Selecione o projeto adicionado (da Etapa 6) e clique **em Vincular**.<br />15. Selecione a localização original.|Solução e projetos permanecem controlados.|

## <a name="see-also"></a>Confira também
- [Guia de teste para plug-ins de controle do código-fonte](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
