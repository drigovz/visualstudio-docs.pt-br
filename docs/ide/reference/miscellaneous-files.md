---
title: Arquivos diversos
description: Saiba como trabalhar em arquivos que não estão incluídos em um projeto ou solução do Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.newfile
- VS.OpenWith
- MiscellaneousFilesProject
helpviewer_keywords:
- solutions, miscellaneous files
- standalone files
- Solution Explorer, miscellaneous files
- Miscellaneous Files folder
- files [Visual Studio], miscellaneous
ms.assetid: 5b96640b-8efe-48a4-8d0a-1ae3f9587e44
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7a8257dad083378c9e4454f0c048fea7ed06e2dd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99902766"
---
# <a name="miscellaneous-files"></a>Arquivos diversos

Talvez você queira usar o editor do Visual Studio para trabalhar de forma independente nos arquivos de um projeto ou de uma solução. Enquanto você tiver uma solução aberta, pode abrir e modificar arquivos sem adicioná-los a uma solução ou um projeto. Os arquivos com os quais você deseja trabalhar independentemente são chamados de arquivos diversos. Os arquivos diversos são externos às soluções e projetos, não estão incluídos em builds e não podem ser incluídos com uma solução sob controle do código-fonte.

Abrir arquivos independentemente de um projeto ou solução é útil para uma variedade de razões. Você pode ter um arquivo que deseja exibir enquanto desenvolve uma solução baseada em projeto, mas que não é parte integrante do desenvolvimento da solução. Exemplos comuns incluem instruções ou anotações de desenvolvimento, esquema de banco de dados e fragmentos de código. Além disso, você talvez queira criar um arquivo autônomo.

![Projetos de soluções](../../ide/reference/media/projects_solutions_misc.gif)

O Gerenciador de Soluções poderá exibir uma pasta **Arquivos Diversos** para os arquivos se as opções para a pasta estiverem habilitadas. As opções podem ser definidas em [Caixa de diálogo Documentos, Ambiente, Opções](../../ide/reference/documents-environment-options-dialog-box.md). Depois de fechar um arquivo diverso, ele não é associado a nenhuma solução ou projeto específico, a menos que uma opção seja habilitada para isso também.

A pasta **Arquivos Diversos** representa os arquivos como links. Embora essa pasta não seja parte de uma solução, quando você abre uma solução, alguns ou todos os arquivos diversos que estavam abertos quando a solução foi fechada pela última vez são reabertos, dependendo das configurações da pasta.

> [!NOTE]
> Alguns dos arquivos que não aparecem na pasta **Arquivos Diversos** são arquivos que você não pode modificar dentro do IDE, como arquivos .zip e arquivos .doc. O IDE não rastreia arquivos que podem ser modificados apenas por um editor externo.

## <a name="commands-available-in-the-ide"></a>Comandos disponíveis no IDE

Os menus, barras de ferramentas e os comandos que eles contêm mudam com base no formato do arquivo aberto. Quando você abre um arquivo de texto, por exemplo, a barra de ferramentas Editor de Texto aparece e seus comandos estão disponíveis. Se você abrir um arquivo de Esquema XML, a barra de ferramentas Esquema XML será exibida. Ao editar o Esquema XML, os comandos da barra de ferramentas Editor de Texto (ou a barra de ferramentas em si) estão indisponíveis. O Esquema XML é a janela ativa e como tal, tem contexto de seleção atual. Quando você muda entre um arquivo de projeto e um arquivo diverso, todos os comandos relacionados ao projeto desaparecem e somente aqueles que estão diretamente relacionados aos arquivos diversos são exibidos.

## <a name="folder-display-options"></a>Opções de exibição de pasta

Você pode definir opções de exibição para a pasta **Arquivos Diversos** para que ela seja exibida mesmo que você não tenha aberto nenhum arquivo diverso. O arquivo de solução não gerencia permanentemente uma lista de arquivos diversos. Ele usa um recurso opcional que permite que ele se lembre uma lista de arquivos MRU (recentemente usados) por usuário.

## <a name="see-also"></a>Confira também

- [Desenvolver código no Visual Studio sem projetos nem soluções](../develop-code-in-visual-studio-without-projects-or-solutions.md)
- [Soluções e projetos](../../ide/solutions-and-projects-in-visual-studio.md)
- [Caixa de diálogo Documentos, Ambiente, Opções](../../ide/reference/documents-environment-options-dialog-box.md)
