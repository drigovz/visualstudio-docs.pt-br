---
title: Como desabilitar o processo de hospedagem | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- hosting process, disabling
- vshost.exe, disabling the hosting process
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 95dcd7da113bfe996d00e617b7c8e2f9b68864d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667970"
---
# <a name="how-to-disable-the-hosting-process"></a>Como desabilitar o processo de hospedagem
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chamadas para determinadas APIs podem ser afetadas quando o processo de hospedagem está habilitado. Nesses casos, é necessário desabilitar o processo de hospedagem para retornar os resultados corretos.

### <a name="to-disable-the-hosting-process"></a>Para desabilitar o processo de hospedagem

1. Abra um projeto executável em [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Projetos que não geram executáveis (por exemplo, projetos de serviço ou biblioteca de classes) não têm essa opção.

2. No menu **Projeto** , clique em **Propriedades**.

3. Clique na guia **Depurar**.

4. Desmarque a caixa de seleção **Habilitar o processo de hospedagem do Visual Studio**.

   Quando o processo de hospedagem é desabilitado, vários recursos de depuração ficam não disponíveis ou apresentam um desempenho reduzido. Para obter mais informações, consulte [depuração e o processo de hospedagem](../debugger/debugging-and-the-hosting-process.md).

   De modo geral, quando o processo de hospedagem está desabilitado:

- O tempo necessário para iniciar a depuração de aplicativos [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] aumenta.

- A avaliação de expressões em tempo de design fica não disponível.

- A depuração de confiança parcial ficará não disponível.

## <a name="see-also"></a>Consulte Também
 [Depuração e o processo de hospedagem do processo de hospedagem](../debugger/debugging-and-the-hosting-process.md) [(vshost.exe)](../ide/hosting-process-vshost-exe.md) [compila durante o desenvolvimento do aplicativo](https://msdn.microsoft.com/c9497d62-3b7b-4449-88e8-cf27acc9efe6)
