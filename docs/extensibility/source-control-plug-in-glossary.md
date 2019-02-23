---
title: Glossário do plug-in de controle de origem | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- glossary [Visual Studio SDK]
- source control plug-ins, glossary
ms.assetid: f224bbc9-38fc-4c80-ab09-51dcc8969f8e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0df624a27513fa0eb18b2643bb7c680d71d94c0c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/22/2019
ms.locfileid: "56722350"
---
# <a name="source-control-plug-in-glossary"></a>Glossário de plug-in de controle do código-fonte
Os seguintes termos úteis e definições referem-se a documentação do SDK de plug-in de controle do código-fonte.

## <a name="definitions"></a>Definições
 Check-in quando um usuário faz alterações em uma cópia de trabalho, um usuário deve enviar as alterações da cópia funcional para o repositório de controle de origem central. Isso cria uma nova revisão do arquivo que está disponível para outros usuários. Esse processo é chamado um check-in.

 Check-out o ato de solicitar uma cópia de trabalho do repositório, informando o repositório de sua intenção de modificá-lo. Uma cópia funcional reflete o estado do projeto a partir do momento em que ele foi extraído.

 Programa de cliente A que usa o sistema de controle do código-fonte. Para fins desta documentação é o IDE do Visual Studio.

 Mensagem de comentário um que descreve as alterações que um usuário pode se conectar a uma revisão quando uma operação de controle do código-fonte é executada.

 Conflito A situação em que dois usuários tentam fazer check-in é alterado para a mesma região do mesmo arquivo. Normalmente, uma mesclagem deve ser executada.

 Pasta local do diretório um lado do cliente é chamada de um diretório. Esta é a cópia no qual um usuário, na verdade, faz alterações. Pode haver muitas cópias de trabalho de um determinado projeto; em geral, cada desenvolvedor tem sua própria cópia.

 Operação de obtenção de um GET traz cópia de trabalho do usuário atualizada com a cópia do repositório. Ao contrário de um check-out, um get é executado quando o usuário simplesmente precisa a cópia mais recente, mas pretende sem fazer alterações.

 Histórico de normalmente é um resumo de todos os check-outs, check-ins, atualizações, marcas e versões feitas no repositório de controle de origem.

 IDE geralmente se refere ao Visual Studio Integrated Development Environment. No entanto, ela pode também se referir a outros ambientes de cliente que reconhecem a API de plug-in de controle do código-fonte.

 Mescle o processo durante a qual fonte de dois ou mais arquivos de código são combinados para formar um novo arquivo que incorpora a todos os recursos de arquivos anteriores. Esse conceito é vital em controle de versão em que dois ou mais desenvolvedores trabalham em arquivos simultaneamente.

 Pasta de controle de origem do projeto A é conhecida como um projeto. Isso não tem nenhuma relação com projetos ou soluções no Visual Studio.

 Plug-in de uma DLL que fornece funcionalidade de controle do código-fonte, Implementando a API de plug-in de controle do código-fonte.

 Repositório a cópia mestra em que um sistema de controle do código-fonte armazena o histórico de revisão completa de um projeto. Cada projeto tem exatamente um repositório.

 Revisão de um compromisso de alteração no histórico de um arquivo ou conjunto de arquivos. Uma revisão é um instantâneo em um projeto continuamente em alteração.

## <a name="see-also"></a>Consulte também
- [Plug-ins de controle do código-fonte](../extensibility/source-control-plug-ins.md)