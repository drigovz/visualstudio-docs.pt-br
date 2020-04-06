---
title: MSSCCPRJ. Arquivo SCC | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, MSSCCPRJ.SCC file
- MSSCCPRJ.SCC file
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89511b7c8b69c5793eceef7d58153dde253a4f47
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702466"
---
# <a name="mssccprjscc-file"></a>MSSCCPRJ. Arquivo SCC
Quando você coloca uma solução ou projeto do Visual Studio sob controle de origem usando o IDE, o IDE recebe duas informações-chave. A informação vem do plug-in de controle de origem na forma de strings. Essas strings, "AuxPath" e "ProjName", são opacas ao IDE, mas são usadas pelo plug-in para localizar a solução ou o projeto no controle de versão. O IDE normalmente recebe essas strings pela primeira vez chamando o [SccGetProjPath](../extensibility/sccgetprojpath-function.md)e, em seguida, salva-os na solução ou arquivo de projeto para chamadas futuras para o [SccOpenProject](../extensibility/sccopenproject-function.md). Quando incorporados nos arquivos de solução e projeto, as strings "AuxPath" e "ProjName" não são atualizadas automaticamente quando um usuário ramifica, bifurca ou copia arquivos de solução e projeto que estão no controle de versão. Para garantir que a solução e os arquivos do projeto apontem para sua localização correta no controle da versão, os usuários devem atualizar manualmente as strings. Como as cordas são feitas para serem opacas, pode nem sempre ficar claro como elas devem ser atualizadas.

 O plug-in de controle de origem pode evitar esse problema armazenando as strings "AuxPath" e "ProjName" em um arquivo especial chamado arquivo *MSSCCPRJ.SCC.* É um arquivo local, do lado do cliente, que é de propriedade e mantido pelo plug-in. Este arquivo nunca é colocado sob controle de origem, mas é gerado pelo plug-in para cada diretório que contenha arquivos controlados por origem. Para determinar quais arquivos são a solução visual studio e arquivos de projeto, um plug-in de controle de origem pode comparar as extensões de arquivo com uma lista padrão ou fornecida pelo usuário. Uma vez que o IDE detecta que um plug-in suporta o arquivo *MSSCCPRJ.SCC,* ele deixa de incorporar as seqüências "AuxPath" e "ProjName" em arquivos de solução e projeto, e ele lê essas strings do arquivo *MSSCCPRJ.SCC* em vez disso.

 Um plug-in de controle de origem que suporte o arquivo *MSSCCPRJ.SCC* deve seguir as seguintes diretrizes:

- Só pode haver um arquivo *MSSCCPRJ.SCC* por diretório.

- Um arquivo *MSSCCPRJ.SCC* pode conter o "AuxPath" e "ProjName" para vários arquivos que estão sob controle de origem dentro de um determinado diretório.

- A seqüência "AuxPath" não deve ter aspas dentro dele. É permitido ter citações ao seu redor como delimitadores (por exemplo, um par de aspas duplas pode ser usado para indicar uma seqüência vazia). O IDE removerá todas as citações da seqüência "AuxPath" quando for lida no arquivo *MSSCCPRJ.SCC.*

- A seqüência "ProjName" no *MSSCCPRJ. O arquivo SCC* deve corresponder exatamente `SccGetProjPath` à seqüência retornada da função. Se a seqüência retornada pela função tiver citações ao seu redor, a seqüência no arquivo *MSSCCPRJ.SCC* deve ter citações em torno dele, e vice-versa.

- Um arquivo *MSSCCPRJ.SCC* é criado ou atualizado sempre que um arquivo é colocado sob controle de origem.

- Se um arquivo *MSSCCPRJ.SCC* for excluído, um provedor deve regenerá-lo na próxima vez que realizar uma operação de controle de origem sobre esse diretório.

- Um arquivo *MSSCCPRJ.SCC* deve seguir estritamente o formato definido.

## <a name="an-illustration-of-the-mssccprjscc-file-format"></a>Uma ilustração do MSSCCPRJ. Formato de arquivo SCC
 A seguir está uma amostra do formato de arquivo *MSSCCPRJ.SCC* (os números de linha são fornecidos apenas como guia e não devem ser incluídos no corpo do arquivo):

- [Linha 1]`SCC = This is a Source Code Control file`

- [Linha 2]

- [Linha 3]`[TestApp.sln]`

- [Linha 4]`SCC_Aux_Path = "\\server\vss\"`

- [Linha 5]`SCC_Project_Name = "$/TestApp"`

- [Linha 6]

- [Linha 7]`[TestApp.csproj]`

- [Linha 8]`SCC_Aux_Path = "\\server\vss\"`

- [Linha 9]`SCC_Project_Name = "$/TestApp"`

 A primeira linha afirma o propósito do arquivo e serve como assinatura para todos os arquivos deste tipo. Esta linha deve aparecer exatamente assim em todos os arquivos *MSSCCPRJ.SCC:*

 `SCC = This is a Source Code Control file`

 A seção a seguir detalha as configurações de cada arquivo, marcadapelo nome do arquivo em colchetes quadrados. Esta seção é repetida para cada arquivo que está sendo rastreado. Esta linha é uma amostra de `[TestApp.csproj]`um nome de arquivo, ou seja, . O IDE espera as duas linhas seguintes. Não define, no entanto, o estilo dos valores definidos. As variáveis `SCC_Aux_Path` são `SCC_Project_Name`e .

 `SCC_Aux_Path = "\\server\vss\"`

 `SCC_Project_Name = "$/TestApp"`

 Não há delimitador final para esta seção. O nome do arquivo, bem como todos os literais que aparecem no arquivo, são definidos no arquivo de cabeçalho scc.h. Para obter mais informações, consulte [Strings usados como chaves para encontrar um plug-in de controle de origem](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md).

## <a name="see-also"></a>Confira também
- [Plug-ins de controle de origem](../extensibility/source-control-plug-ins.md)
- [Cordas usadas como chaves para encontrar um plug-in de controle de origem](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)
