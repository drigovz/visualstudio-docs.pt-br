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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 69511c2f83570abf37ef4bea8b71c8f59431a128
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72729569"
---
# <a name="source-server-security-alert"></a>Alerta de segurança do servidor de origem
Ao usar o Servidor de Origem, use somente os arquivos de símbolo que forem de um local conhecido e confiável.

 Este aviso aparece quando você ativa o suporte do servidor de origem. Os comandos do servidor de origem são inseridos nos arquivos de símbolo de depuração (arquivos** \* . pdb** ). Verifique se você sabe de onde vêm seus arquivos PDB.

> [!IMPORTANT]
> As seguintes riscos de segurança devem ser levadas em consideração ao usar o servidor de origem: os comandos arbitrários podem ser inseridos no arquivo de PDB do aplicativo, de forma que você coloque somente aqueles que você deseja executar no arquivo de srcsrv.ini. Qualquer tentativa de executar um comando que não esteja no arquivo srcsvr.ini fará com que uma caixa de diálogo de confirmação seja exibida. Para obter mais informações, consulte [aviso de segurança: o depurador deve executar o comando não confiável](../debugger/security-warning-debugger-must-execute-untrusted-command.md). Nenhuma validação é feita em parâmetros do comando. Portanto, tenha cuidado com comandos confiáveis. Por exemplo, se você confiar no cmd.exe, um usuário mal-intencionado pode especificar parâmetros que tornariam o comando perigoso.

## <a name="see-also"></a>Confira também
- [Especificar os arquivos de origem e símbolo (.pdb)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
- [Segurança do depurador](../debugger/debugger-security.md)
- [Servidor de origem](/windows/desktop/Debug/source-server-and-source-indexing)
