---
title: Decisões de design do tipo de projeto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, project file persistence
- project types, commitment mechanics
- project types, items
- project types, design decisions
ms.assetid: f68671fe-fd7a-4e56-a0b5-330b0f1fedb1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5e33ac1c4168593b881f799dfdfb94005fb55fc1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706369"
---
# <a name="project-type-design-decisions"></a>Decisões de design do tipo de projeto
Antes de criar um novo tipo de projeto, você deve tomar várias decisões de design em relação ao seu tipo de projeto. Você deve decidir quais tipos de itens seus projetos conterão, como os arquivos do projeto serão persistidos e qual modelo de compromisso você usará.

## <a name="project-items"></a>Itens de projeto
 Seu projeto usará arquivos ou objetos abstratos? Se você usar arquivos, eles serão arquivos baseados em referência ou baseados em diretórios? Os arquivos ou objetos abstratos serão locais ou remotos?

 Os itens em um projeto podem ser arquivos, ou podem ser objetos mais abstratos, como objetos em um repositório de banco de dados ou conexões de dados na Internet. Se os itens forem arquivos, o projeto pode ser baseado em referência ou em um projeto baseado em diretório.

 Em projetos baseados em referência, os itens podem aparecer em mais de um projeto. No entanto, o arquivo real que um item representa está localizado apenas em um diretório. Em projetos baseados em diretórios, todos os itens do projeto existem na estrutura do diretório.

 Os itens locais são armazenados no mesmo computador onde o aplicativo está instalado. Itens remotos podem ser armazenados em um servidor separado em uma rede local ou em outros lugares da Internet.

## <a name="project-file-persistence"></a>Persistência de arquivo de projeto
 Os dados serão armazenados em sistemas de arquivos planos comuns ou em armazenamento estruturado? Os arquivos serão abertos usando um editor padrão ou um editor específico de projeto?

 Para persistir seus dados, a maioria dos aplicativos salva seus dados em um arquivo e, em seguida, lê-los de volta quando um usuário deve rever ou alterar as informações.

 O armazenamento estruturado, também chamado de arquivos compostos, é normalmente usado quando vários objetos com (Component Object Model, modelo de objeto componente) precisam armazenar seus dados persistindo em um único arquivo. Com o armazenamento estruturado, vários componentes de software diferentes podem compartilhar um único arquivo de disco.

 Você tem várias opções a considerar em relação à persistência para os itens do seu projeto. Você pode executar qualquer uma das seguintes opções:

- Salve cada arquivo individualmente quando ele tiver sido alterado.

- Capture muitas transações em uma única operação **Salvar.**

- Salve arquivos localmente e publique em um servidor ou use outra abordagem para salvar itens do projeto quando o item representar uma conexão de dados a um objeto remoto.

  Para obter mais informações sobre persistência, consulte [Project Persistence](../../extensibility/internals/project-persistence.md) and [Opening and Saving Project Its](../../extensibility/internals/opening-and-saving-project-items.md).

## <a name="project-commitment-model"></a>Modelo de Compromisso do Projeto
 Os objetos de dados persistidos serão abertos no modo direto ou no modo transacionado?

 Quando os objetos de dados são abertos no modo direto, as alterações feitas nos dados são incorporadas imediatamente ou quando o usuário salva manualmente o arquivo.

 Quando os objetos de dados são abertos usando o modo transacionado, as alterações são salvas em um local temporário na memória e não são cometidas até que o usuário escolha manualmente salvar o arquivo. Nesse momento, todas as mudanças devem ocorrer em conjunto ou nenhuma mudança será feita.

## <a name="see-also"></a>Confira também
- [Lista de verificação: criando novos tipos de projeto](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Abrindo e salvando itens de projeto](../../extensibility/internals/opening-and-saving-project-items.md)
- [Persistência de projeto](../../extensibility/internals/project-persistence.md)
- [Elementos de um modelo de projeto](../../extensibility/internals/elements-of-a-project-model.md)
- [Componentes principais do projeto modelo](../../extensibility/internals/project-model-core-components.md)
- [Criando tipos de projeto](../../extensibility/internals/creating-project-types.md)
