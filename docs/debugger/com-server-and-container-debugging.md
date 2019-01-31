---
title: Servidor COM e contêiner depuração | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- COM servers, debugging
- ActiveX controls, debugging
- COM [Visual Studio], debugging
ms.assetid: b7ce8696-ebb8-4354-a767-f76b8ada4ac1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9e6969d8bf49390e0dd79a1a201e272bc0aae84e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55015284"
---
# <a name="com-server-and-container-debugging"></a>Depuração de servidor COM e contêiner
Os aplicativos COM executam um número de tarefas fora do controle direto do programador. A comunicação entre DLL, as contagens de uso em objetos e as operações da área de transferência são apenas algumas das áreas onde você pode encontrar comportamento inesperado. Quando isso acontece, a primeira etapa é rastrear a origem do problema.  
  
 O depurador do Visual Studio oferece suporte à depuração em contêineres e servidores. Isso inclui a capacidade de depurar as chamadas de procedimento remoto (RPC).  
  
##  <a name="BKMK_COMServerandContainerintheSameSolution"></a> Depurando um servidor COM e um contêiner na mesma solução  
 Você pode depurar um servidor COM e um contêiner usando dois projetos dentro da mesma solução. Defina pontos de interrupção apropriados em cada projeto e depuração. Quando o contêiner faz uma chamada no servidor que atinge um ponto de interrupção, ele aguardará até que o código de servidor retorne (ou seja, até você concluir a depuração).  
  
 Depurar um contêiner COM é semelhante a depurar um programa padrão. Uma diferença é quando você depura um evento que gera um retorno de chamada (por exemplo, arrastar dados sobre o aplicativo de contêineres). Nesse caso, você deve definir um ponto de interrupção na função de retorno de chamada.  
  
##  <a name="BKMK_ServerApplicationWithoutContainerInformation"></a> Depurando um aplicativo para servidores sem informações de contêiner  
 Se você não tiver ou não desejar usar informações de depuração para seu aplicativo de contêiner, começar a depurar o aplicativo de servidor é um processo de três etapas:  
  
1.  Inicie a depuração do servidor como um aplicativo normal.  
  
2.  Defina pontos de interrupção como desejados.  
  
3.  Inicie o aplicativo de contêiner.  
  
##  <a name="BKMK_DebuggingaServerandDomainIsolationSDIApplication"></a> Depurando um aplicativo para servidores e isolamento de domínio (SDI)  
 Se estiver depurando um aplicativo para servidores de SDI, especifique `/Embedding` ou `/Automation` na propriedade **Argumentos de linha de comando** na caixa de diálogo Páginas de Propriedades de *Projeto* de projetos C/C++, C# ou do Visual Basic.  
  
 Com esses argumentos de linha de comando, o depurador pode iniciar o aplicativo de servidor como se tivesse sido iniciado de um contêiner. Iniciar o contêiner do Gerenciador de Programas ou do Gerenciador de Arquivos fará com que o contêiner use a instância do servidor iniciada no depurador.  
  
 Para acessar a caixa de diálogo Páginas de Propriedades de *Projeto*, clique com o botão direito do mouse no projeto no Gerenciador de Soluções e escolha Propriedades no menu de atalho. Para localizar a propriedade Argumentos de linha de comando, expanda a categoria Propriedades de Configuração e clique na página Depuração.  
  
## <a name="see-also"></a>Consulte também  
 [Depuração de COM e ActiveX](../debugger/com-and-activex-debugging.md)