---
title: Controle de versão
description: Usando o Git e o Subversion no Visual Studio para Mac.
ms.topic: overview
author: jmatthiesen
ms.author: jomatthi
ms.date: 05/06/2018
ms.assetid: 49917483-28AA-4598-A847-71F1F2E0DCB5
ms.openlocfilehash: 9206ab892ef125706ab16f9a739fe88a52f5c242
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "70108105"
---
# <a name="version-control"></a>Controle de versão

O controle de versão é um sistema para gerenciar arquivos em várias versões diferentes e, no desenvolvimento de software, geralmente tem a contribuição de muitos desenvolvedores. O objetivo da entidade de qualquer sistema de controle de versão (_VCS_) é encontrar uma solução que permite que todos os usuários trabalhem na base de código ao mesmo tempo.

O núcleo de qualquer sistema de controle de versão é um _repositório_, que atua como o armazenamento de dados central para todos os diferentes arquivos, de forma semelhante a um servidor de arquivos. No entanto, diferente de um servidor de arquivos, o repositório contém todo o histórico do projeto e todas as revisões que foram feitas.

Se o repositório for um armazenamento de dados central, é lógico que cada usuário tenha um repositório local dos dados para que eles possam trabalhar nele. Isso é chamado de uma _cópia funcional_. No Visual Studio para Mac, sua cópia funcional será exibida da mesma forma que qualquer outro diretório local em seu computador, permitindo que você possa ler e gravar em qualquer um dos arquivos. No entanto, como o Visual Studio para Mac tem integração do sistema de Controle de versão, você pode usar o Subversion e o Git sem deixar o IDE.

O Subversion é um sistema centralizado de controle de versões, o que significa que há um único servidor que contém todos os arquivos e as revisões do qual os usuários podem fazer check-out de qualquer versão de qualquer arquivo. Ao fazer check-out de arquivos de um repositório Subversion remoto, o usuário receberá um instantâneo do repositório no momento em questão.

O Git é um sistema de controle de versão distribuído que permite que as equipes trabalhem nos mesmos documentos simultaneamente. Com o Git, pode haver um único servidor que contém todos os arquivos, mas o repositório inteiro está clonado localmente para seu computador sempre que um repositório passar por check-out dessa fonte central.

## <a name="basic-concepts"></a>Conceitos básicos

O Visual Studio para Mac dá suporte aos sistemas de controle de versão do Git e do Subversion. O artigos a seguir exploram a configuração de repositórios do Git e do Subversion por meio do Visual Studio para Mac, bem como funcionalidades simples como revisar, confirmar e efetuar push nas alterações.

* [Configurando um Repositório Git](set-up-git-repository.md)
* [Trabalhando com Git](working-with-git.md)
* [Configurando um Repositório do Subversion](set-up-subversion-repository.md)
* [Trabalhando com o Subversion](working-with-subversion.md)

## <a name="see-also"></a>Confira também

* [Controle de versão no Visual Studio (no Windows)](/visualstudio/version-control/)