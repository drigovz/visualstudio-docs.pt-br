---
title: 'Como: Depurar um motor de depuração personalizado | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c79790bfc9c9cd3767a453258b8c2d340f64d029
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738580"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Como: Depurar um mecanismo de depuração personalizado
Um tipo de projeto lança o mecanismo <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> de depuração (DE) a partir do método. Isso significa que o DE é lançado [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sob o controle da instância de controle do tipo de projeto. No entanto, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] essa instância de não pode depurar o DE. O que se segue são os passos que permitem que você depuraseu DE Personalizado.

> [!NOTE]
> : No procedimento "Depurar um motor de depuração personalizado", você deve esperar que o DE comece antes de poder anexá-lo. Se você colocar uma caixa de mensagem perto do início do seu DE que aparece quando o DE é iniciado, você pode anexar nesse ponto e, em seguida, limpar a caixa de mensagem para continuar. Dessa forma, você pode pegar todos os eventos DE.

> [!WARNING]
> Você deve ter a depuração remota instalada antes de tentar os seguintes procedimentos. Consulte [Depuração remota](../../debugger/remote-debugging.md) para obter detalhes.

## <a name="debug-a-custom-debug-engine"></a>Depurar um motor de depuração personalizado

1. Iniciar *msvsmon.exe*, o Monitor de depuração remota.

2. No menu **Ferramentas** em *msvsmon.exe, selecione* **Opções** para abrir a caixa de diálogo **Opções.**

3. Selecione a opção "sem autenticação" e clique em **OK**.

4. Inicie uma [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] instância e abra seu projeto DE personalizado.

5. Inicie uma segunda [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] instância e abra seu projeto personalizado que lança o DE (para desenvolvimento, isso é tipicamente na colmeia de registro experimental que é configurada quando o VSIP é instalado).

6. Nesta segunda instância [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]de , carregue um arquivo de origem do seu projeto personalizado e inicie o programa a ser depurado. Aguarde alguns momentos para permitir que o DE carregue ou espere até que um ponto de ruptura seja atingido.

7. Na primeira instância [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] de (com o projeto DE), **selecione Anexar ao processo** no menu **Depuração.**

8. Na caixa de diálogo **Anexar ao processo,** altere o **Transporte** para **Remoto (nativo apenas sem autenticação)**.

9. Altere o **Qualificador** para o nome da sua máquina (nota: há um histórico de entradas, então você precisa digitar este nome apenas uma vez).

10. Na lista **Processos Disponíveis,** selecione a instância do SEU DE que está sendo executado e clique no botão **Anexar.**

11. Depois que os símbolos tiverem sido carregados em seu DE, coloque pontos de interrupção no seu código DE.

12. Toda vez que você parar e reiniciar o processo de depuração, repita as etapas 6 a 10.

## <a name="debug-a-custom-project-type"></a>Depurar um tipo de projeto personalizado

1. Inicie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] na colmeia de registro normal e carregue seu projeto do tipo de projeto (isto é, a fonte para o seu tipo de projeto, não uma instanciação do seu tipo de projeto).

2. Abra as propriedades do Projeto e vá para a página **Depuração.** Para o **Comando,** digite [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] o caminho para o IDE (por padrão, este é *[unidade]* \Arquivos do programa\Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8\Common7\IDE\devenv.exe).

3. Para os **Argumentos** `/rootsuffix exp` de Comando , digite para a colmeia de registro experimental (criada quando o VSIP foi instalado).

4. Clique em **OK** para aceitar as alterações.

5. Inicie seu tipo de projeto pressionando **F5**. Isso lança uma segunda [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]instância de .

6. Neste ponto, você pode colocar pontos de interrupção no código-fonte do tipo de projeto.

7. Na segunda instância [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]de , carregue ou crie uma nova instância do seu tipo de projeto. Durante a carga ou criação, seus pontos de interrupção podem ser atingidos.

8. Depurar seu tipo de projeto.

9. Se você optar por depurar o processo de lançamento de um DE, você pode executar as etapas no procedimento "Depurar um mecanismo de depuração personalizado" para anexar ao seu DE depois que ele for lançado. Isso lhe dá [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] três instâncias de execução: uma para a fonte do seu tipo de projeto, uma segunda para o seu tipo de projeto instanciado e uma terceira anexada ao seu DE.

## <a name="see-also"></a>Confira também
- [Criando um mecanismo de depuração personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)
