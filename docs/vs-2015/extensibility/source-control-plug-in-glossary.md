---
title: Glossário de plug-in de controle do código-fonte | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f5120a5c6678cac32ef65e08ef7dc34649364cf9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160598"
---
# <a name="source-control-plug-in-glossary"></a>Glossário de plug-in de controle do código-fonte
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os termos e definições úteis a seguir pertencem à documentação do SDK de plug-in de controle do código-fonte.  
  
## <a name="definitions"></a>Definições  
 Ins  
 Quando um usuário faz alterações em uma cópia de trabalho, um usuário deve enviar alterações da cópia de trabalho para o repositório do controle do código-fonte central. Isso cria uma nova revisão do arquivo que está disponível para outros usuários. Esse processo é chamado de check-in.  
  
 Check-out  
 O ato de solicitar uma cópia de trabalho do repositório, informando o repositório de sua intenção de modificá-la. Uma cópia de trabalho reflete o estado do projeto a partir do momento em que é feito o check-out.  
  
 Cliente  
 Um programa que usa o sistema de controle do código-fonte. Para a finalidade desta documentação, é o IDE do Visual Studio.  
  
 Comentário  
 Uma mensagem que descreve as alterações que um usuário pode anexar a uma revisão quando uma operação de controle do código-fonte é executada.  
  
 Conflito  
 Uma situação em que dois usuários tentam fazer check-in de alterações na mesma região do mesmo arquivo. Normalmente, uma mesclagem deve ser executada.  
  
 Diretório  
 Uma pasta local do lado do cliente é conhecida como um diretório. Essa é a cópia na qual um usuário realmente faz alterações. Pode haver muitas cópias de trabalho de um determinado projeto; em geral, cada desenvolvedor tem sua própria cópia.  
  
 Obter  
 Uma operação get leva a cópia de trabalho do usuário atualizada com a cópia do repositório. Ao contrário de um check-out, um get é executado quando o usuário simplesmente precisa da cópia mais recente, mas pretende não fazer nenhuma alteração.  
  
 Histórico  
 Normalmente, é um resumo de todos os check-outs, check-ins, atualizações, marcas e versões feitas no repositório do controle do código-fonte.  
  
 IDE  
 Geralmente refere-se ao ambiente de desenvolvimento integrado do Visual Studio. No entanto, também pode se referir a outros ambientes de cliente que reconheçam a API de plug-in de controle do código-fonte.  
  
 Mesclar  
 O processo durante o qual dois ou mais arquivos de código-fonte são combinados para formar um novo arquivo que incorpora todos os recursos dos arquivos anteriores. Esse conceito é vital no controle de versão, onde dois ou mais desenvolvedores trabalham em arquivos simultaneamente.  
  
 Project  
 Uma pasta de controle do código-fonte geralmente é chamada de projeto. Isso não tem nenhuma relação com projetos ou soluções no Visual Studio.  
  
 Plug-in  
 Uma DLL que fornece funcionalidade de controle do código-fonte implementando a API de plug-in de controle do código-fonte.  
  
 Repositório  
 A cópia mestra em que um sistema de controle do código-fonte armazena o histórico de revisão completo de um projeto. Cada projeto tem exatamente um repositório.  
  
 Revisão  
 Uma alteração confirmada no histórico de um arquivo ou conjunto de arquivos. Uma revisão é um instantâneo em um projeto de alteração contínua.  
  
## <a name="see-also"></a>Consulte Também  
 [Plug-ins de controle do código-fonte](../extensibility/source-control-plug-ins.md)
