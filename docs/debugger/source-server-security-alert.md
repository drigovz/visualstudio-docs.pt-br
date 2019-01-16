---
title: Alerta de segurança do servidor de origem | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.enablewarning
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 8451c281-6914-469c-b80c-6271cc3f3d17
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e01f9c06ec989829a27c58b7dae9b128512911e9
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2019
ms.locfileid: "53909894"
---
# <a name="source-server-security-alert"></a>Alerta de segurança do servidor de origem
Ao usar o Servidor de Origem, use somente os arquivos de símbolo que forem de um local conhecido e confiável.  
  
 Este aviso aparece quando você ativa o suporte do servidor de origem. Os comandos do servidor de origem são inseridos nos arquivos de símbolo de depuração (arquivos **\*.pdb**). Verifique se você sabe de onde vêm seus arquivos PDB.  
  
> [!IMPORTANT]
>  As seguintes ameaças potenciais de segurança devem ser levadas em conta ao usar o servidor de origem: Os comandos arbitrários podem ser inseridos no arquivo .pdb do aplicativo, portanto, certifique-se de colocar somente aqueles que você deseja executar no arquivo srcsrv.ini. Qualquer tentativa de executar um comando que não esteja no arquivo srcsvr.ini fará com que uma caixa de diálogo de confirmação seja exibida. Para obter mais informações, consulte [aviso de segurança: O depurador precisa executar um comando não confiável](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Nenhuma validação é feita em parâmetros do comando. Portanto, tenha cuidado com comandos confiáveis. Por exemplo, se você confiar no cmd.exe, um usuário mal-intencionado pode especificar parâmetros que tornariam o comando perigoso.  
  
## <a name="see-also"></a>Consulte também  
 [Especificar arquivos de símbolo (.pdb) e de origem](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Segurança do depurador](../debugger/debugger-security.md)   
 [Servidor de Origem](/windows/desktop/Debug/source-server-and-source-indexing)
