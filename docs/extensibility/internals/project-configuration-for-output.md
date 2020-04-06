---
title: Configuração do projeto para saída | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project configurations, output
ms.assetid: a4517f73-45af-4745-9d7f-9fddf887b636
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 78b95457af4c5d806fdfcc20f49ac4e82df36488
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706663"
---
# <a name="project-configuration-for-output"></a>Configuração de projeto para saída
Cada configuração pode suportar um conjunto de processos de compilação que produzem itens de saída, como arquivos executáveis ou de recursos. Esses itens de saída são privados para o usuário e podem ser colocados em grupos que vinculam tipos relacionados de saída, como arquivos executáveis (.exe, .dll, .lib) e arquivos de origem (arquivos .idl, .h).

 Os itens de saída podem <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutput2> ser disponibilizados através dos <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumOutputs> métodos e enumerados com os métodos. Quando você deseja agrupar itens de saída, <xref:Microsoft.VisualStudio.Shell.Interop.IVsOutputGroup> seu projeto também deve implementar a interface.

 A construção desenvolvida `IVsOutputGroup` pela implementação permite que os projetos agrupam as saídas de acordo com o uso. Por exemplo, uma DLL pode ser agrupada com seu banco de dados de programas (PDB).

> [!NOTE]
> Um arquivo PDB contém informações de depuração e é criado quando a opção 'Gerar depuração' é especificada ao construir o .dll ou .exe. O arquivo .pdb geralmente é gerado apenas para a configuração do projeto Debug.

 O projeto deve retornar o mesmo número de grupos para cada configuração que ele suporta, embora o número de saídas contidas em um grupo possa variar de configuração para configuração. Por exemplo, o projeto DLL de Matt pode incluir mattd.dll e mattd.pdb na configuração Debug, mas apenas incluir matt.dll na configuração Destore.

 Os grupos também têm as mesmas informações de identificador, como nome canônico, nome de exibição e informações de grupo, desde a configuração até a configuração dentro de um projeto. Essa consistência permite que a implantação e a embalagem continuem a operar mesmo que as configurações mudem.

 Os grupos também podem ter uma saída de chave que permite que atalhos de embalagem aponte para algo significativo. Qualquer grupo pode estar vazio em uma determinada configuração, então nenhuma suposição deve ser feita sobre o tamanho de um grupo. O tamanho (número de saídas) de cada grupo em qualquer configuração pode ser diferente do tamanho de outro grupo na mesma configuração. Também pode ser diferente do tamanho do mesmo grupo em outra configuração.

 ![Gráfico de grupos de saída](../../extensibility/internals/media/vsoutputgroups.gif "vsOutputGroups") Grupos de saída

 O principal uso <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg> da interface é fornecer acesso à construção, implantação e depuração de objetos de gerenciamento e permitir aos projetos a liberdade de agrupar saídas. Para obter mais informações sobre o uso desta interface, consulte [Project Configuration Object](../../extensibility/internals/project-configuration-object.md).

 No diagrama anterior, o Group Built tem uma saída de chave entre as configurações (bD.exe ou b.exe) para que o usuário possa criar um atalho para Built e saber que o atalho funcionará independentemente da configuração implantada. A Fonte do Grupo não tem uma saída de chave, portanto, o usuário não pode criar um atalho para ela. Se o Grupo de Depuração Construído tiver uma saída chave, mas o Grupo de Varejo Construído não, isso seria uma implementação incorreta. Segue-se, então, que se qualquer configuração tiver um grupo que não contenha saídas e, como resultado, nenhum arquivo-chave, então outras configurações com esse grupo que contenham saídas não podem ter arquivos-chave. Os editores do instalador assumem que nomes canônicos e nomes de exibição de grupos, além da existência de um arquivo-chave, não mudam com base nas configurações.

 Observe que se um `IVsOutputGroup` projeto tem um que ele não quer empacotar ou implantar, basta não colocar essa saída em um grupo. A saída ainda pode ser enumerada <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg.EnumOutputs%2A> normalmente implementando o método que retorna todas as saídas de uma configuração, independentemente do agrupamento.

 Para obter mais informações, `IVsOutputGroup` consulte a implementação da amostra do Projeto Personalizado no [MPF para Projetos](https://github.com/tunnelvisionlabs/MPFProj10).

## <a name="see-also"></a>Confira também
- [Gerenciando opções de configuração](../../extensibility/internals/managing-configuration-options.md)
- [Configuração de projeto para compilar](../../extensibility/internals/project-configuration-for-building.md)
- [Objeto de configuração de projeto](../../extensibility/internals/project-configuration-object.md)
- [Configuração da solução](../../extensibility/internals/solution-configuration.md)
