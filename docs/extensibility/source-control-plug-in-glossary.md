---
title: Glossário plug-in de controle de fonte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3835561eb63fa2a4a71174732c07ecd73f1df5d7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699905"
---
# <a name="source-control-plug-in-glossary"></a>Glossário de plug-in de controle do código-fonte
Os seguintes termos e definições úteis pertencem à documentação sDK plug-in do Controle de Fonte.

## <a name="definitions"></a>Definições
 Checkin Quando um usuário faz alterações em uma cópia de trabalho, um usuário deve enviar alterações da cópia de trabalho para o repositório de controle de origem central. Isso cria uma nova revisão do arquivo que está disponível para outros usuários. Esse processo é chamado de check-in.

 Checkout O ato de solicitar uma cópia de trabalho do repositório, informando o repositório de sua intenção de modificá-lo. Uma cópia de trabalho reflete o estado do projeto a partir do momento em que é verificado.

 Cliente Um programa que usa o sistema de controle de código fonte. Para o efeito desta documentação, é o Visual Studio IDE.

 Comentário Uma mensagem descrevendo as alterações que um usuário pode anexar a uma revisão quando uma operação de controle de origem é realizada.

 Conflito Uma situação em que dois usuários tentam fazer check-in alterações na mesma região do mesmo arquivo. Normalmente, uma fusão deve ser realizada.

 Diretório Uma pasta local do lado do cliente é referida como um diretório. Esta é a cópia em que um usuário realmente faz alterações. Pode haver muitas cópias de trabalho de um determinado projeto; geralmente cada desenvolvedor tem sua própria cópia.

 Obter uma operação get traz a cópia de trabalho do usuário atualizada com a cópia do repositório. Ao contrário de um checkout, um get é realizado quando o usuário simplesmente precisa da cópia mais recente, mas pretende não fazer alterações.

 Histórico É tipicamente um resumo de todos os checkouts, check-ins, atualizações, tags e lançamentos feitos no repositório de controle de origem.

 O IDE geralmente se refere ao Ambiente de Desenvolvimento Integrado do Estúdio Visual. No entanto, ele também pode se referir a outros ambientes de clientes que reconhecem a API plug-in de controle de fonte.

 Mesclar O processo durante o qual dois ou mais arquivos de código-fonte são combinados para formar um novo arquivo que incorpora todos os recursos de arquivos anteriores. Este conceito é vital no controle de versão onde dois ou mais desenvolvedores trabalham em arquivos simultaneamente.

 A pasta de controle de origem do Projeto A é frequentemente referida como um projeto. Isso não tem qualquer relação com projetos ou soluções no Visual Studio.

 Plug-in A DLL que fornece funcionalidade de controle de origem implementando a API plug-in de controle de fonte.

 Repositório A cópia mestre onde um sistema de controle de origem armazena o histórico completo de revisão de um projeto. Cada projeto tem exatamente um repositório.

 Revisão Uma alteração comprometida no histórico de um arquivo ou conjunto de arquivos. Uma revisão é um instantâneo em um projeto em constante mudança.

## <a name="see-also"></a>Confira também
- [Plug-ins de controle do código-fonte](../extensibility/source-control-plug-ins.md)
