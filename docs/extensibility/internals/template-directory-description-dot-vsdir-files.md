---
title: Descrição do diretório de modelos (. Vsdir) Arquivos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .vsdir files
- VSDIR files
- template directory description files
ms.assetid: 9df51800-190e-4662-b685-fdaafcff1400
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 16ba609d5b05d565a12b38bd19e9a777851ced5b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704697"
---
# <a name="template-directory-description-vsdir-files"></a>Arquivos de descrição do diretório de modelo (.Vsdir)
Um arquivo de descrição do diretório de modelo (.vsdir) é um arquivo de texto que permite que o ambiente de desenvolvimento integrado (IDE) exiba pastas, arquivos assistente .vsz e arquivos de modelo associados ao seu projeto em caixas de diálogo. O conteúdo inclui um registro por arquivo ou pasta. Todos os arquivos .vsdir em um local referenciado são mesclados, embora apenas um arquivo .vsdir seja geralmente fornecido para descrever várias pastas, assistentes ou arquivos de modelo.

 Pastas (subdiretórios), arquivos referenciados no arquivo .vsdir e o próprio arquivo .vsdir estão todos localizados no mesmo diretório. Quando o IDE executa um assistente ou exibe uma pasta ou arquivo nas caixas de diálogo **Novo Projeto** ou Adicionar **Novo Item,** o IDE examina o diretório que contém os arquivos executados para determinar se um arquivo .vsdir está presente. Se um arquivo .vsdir for encontrado, o IDE o lerá para determinar se ele contém uma entrada para a pasta ou arquivo executado ou exibido. Se uma entrada for encontrada, o IDE usará as informações na execução do assistente ou exibição do conteúdo.

 O exemplo de código a seguir é do \<arquivo SourceFiles.vsdir no EnvSDK>\BscPrj\BscPrj\BscPrjProjectItems\Source_Files chave de registro:

```
HeaderFile.h|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#125|130|#126|0|0|0|#127
SourceFile.cpp|{E59935A1-6156-11d1-87A6-00A0C91E2A46}|#122|110|#123|0|0|0|#124
```

 Neste caso, dois registros estão em um arquivo. Uma nova linha (caractere de retorno de transporte) separa cada registro. Cada linha representa um tipo de arquivo diferente. Um caractere pipe (&#124;) separa campos em cada registro. Um único diretório pode conter vários arquivos .vsdir que têm nomes de arquivo diferentes, ou você pode ter um arquivo .vsdir para cada tipo de arquivo.

## <a name="fields"></a>Campos
 A tabela a seguir lista os campos especificados para cada registro.

| Campo | Descrição |
| - | - |
| Nome do caminho relativo (RelPathName) | O nome da pasta, modelo ou arquivo .vsz, como HeaderFile.h ou MyWizard.vsz. Este campo também pode ser um nome usado para representar uma pasta. |
| {clsidPackage} | O GUID do VSPackage que permite o acesso a strings localizadas, como LocalizedName, Description, IconResourceId e SuggestedBaseName, nos recursos da Biblioteca de Link Dinâmico de Satélite (DLL) do VSPackage. IconResourceId se aplica se o DLLPath não for fornecido. **Nota:**  Este campo é opcional, a menos que um ou mais dos campos anteriores sejam um identificador de recursos. Este campo é tipicamente em branco para arquivos .vsdir que correspondem a assistentes de terceiros que não localizam seu texto. |
| Localizedname | O nome localizado do arquivo ou assistente do modelo. Este campo pode ser uma seqüência ou um identificador de recursos do formulário "#ResID". Este nome é exibido na caixa de diálogo **Adicionar novo item.** **Nota:**  Se LocalizedName for um identificador de recursos, então {clsidPackage} é necessário. |
| ClassificarPrioridade | Um inteiro representando a prioridade relativa deste arquivo ou assistente de modelo. Por exemplo, se este item tiver um valor de 1, então este item é exibido ao lado de outros itens com um valor de 1 e à frente de todos os itens com um valor de tipo 2 ou maior.<br /><br /> A prioridade de classificação é relativa aos itens do mesmo diretório. Pode haver mais de um arquivo .vsdir no mesmo diretório. Nesse caso, os itens de <em>todos.</em> arquivos vsdir nesse diretório são mesclados. Os itens com a mesma prioridade são listados na ordem lexicográfica insensível do nome exibido. A `_wcsicmp` função é usada para encomendar os itens.<br /><br /> Os itens não descritos em arquivos .vsdir incluem um número de prioridade maior do que o número de prioridade mais alto listado nos arquivos .vsdir. O resultado é que esses itens estão no final da lista exibida, independentemente do nome. |
| Descrição | A descrição localizada do arquivo ou assistente do modelo. Este campo pode ser uma seqüência ou um identificador de recursos do formulário "#ResID". Essa seqüência de string aparece na caixa de diálogo **Novo projeto** ou adicionar **novo item** quando o item é selecionado. |
| DLLPath ou {clsidPackage} | Usado para carregar um ícone para o arquivo de modelo ou assistente. O ícone é carregado como um recurso de um arquivo .dll ou .exe usando o IconResourceId. Este arquivo .dll ou .exe pode ser identificado usando um caminho completo ou usando um GUID de um VSPackage. A implementação DLL do VSPackage é usada para carregar o ícone (não o DLL do satélite). |
| IconResourceId | O identificador de recursos na DLL ou no DLL de implementação do VSPackage que determina o ícone a ser exibido. |
| Bandeiras<xref:Microsoft.VisualStudio.Shell.Interop.__VSDIRFLAGS>( ) | Usado para desativar ou ativar os campos **Nome** e **Local** na caixa de diálogo **Adicionar novo item.** O valor do campo **Bandeiras** é o equivalente decimal da combinação de bandeiras de bits necessárias.<br /><br /> Quando um usuário seleciona um item na guia **Novo,** o projeto determina se o campo Nome e o campo Local são mostrados quando a caixa de diálogo **Adicionar novo item** é exibida pela primeira vez. Um item, através de um arquivo .vsdir, só pode controlar se os campos estão habilitados versus desativados quando o item é selecionado. |
| Nome da Base sugerido | Representa o nome padrão do arquivo, assistente ou modelo. Este campo é uma seqüência ou um identificador de recursos do formulário "#ResID". O IDE usa esse valor para fornecer um nome padrão para o item. Esse valor base é anexado com um valor inteiro para tornar o nome único, como MyFile21.asp.<br /><br /> Na lista anterior, Descrição, DLLPath, IconResourceId, Flags e SuggestedBaseNumber aplicam-se apenas a arquivos de modelo e assistente. Esses campos não se aplicam a pastas. Este fato é ilustrado no código no arquivo BscPrjProjectItems no \<EnvSDK>\BscPrj\BscPrj\BscPrjProjectItems key. Este arquivo contém três registros (um para cada pasta) com quatro campos para cada registro: RelPathName, {clsidPackage}, LocalizedName e SortPriority.<br /><br /> `General&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#110&#124;100`<br /><br /> `Source_Files&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#111&#124;110`<br /><br /> `Env&#124;{E59935A1-6156-11d1-87A6-00A0C91E2A46}&#124;#112&#124;120` |

 Ao criar um arquivo assistente, você também deve considerar os seguintes problemas.

- Qualquer campo não obrigatório para o qual não haja dados significativos deve conter um 0 (zero) como espaço reservado.

- Se nenhum nome localizado for fornecido, o nome do caminho relativo será usado no arquivo assistente.

- DLLPath substitui clsidPacote para localização de ícones.

- Se nenhum ícone for definido, o IDE substituirá o ícone padrão por um arquivo que tenha essa extensão.

- Se nenhum nome base sugerido for fornecido, 'Projeto' será usado.

- Se você excluir os arquivos .vsz, pastas ou arquivos de modelo, você também deve remover seus registros associados do arquivo .vsdir.

## <a name="see-also"></a>Confira também
- [Assistentes](../../extensibility/internals/wizards.md)
- [Arquivo do assistente (.Vsz)](../../extensibility/internals/wizard-dot-vsz-file.md)
