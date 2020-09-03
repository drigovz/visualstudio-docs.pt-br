---
title: '&lt;&gt;elemento File (aplicativo ClickOnce) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- http://www.w3.org/2000/09/xmldsig#Transform
- urn:schemas-microsoft-com:asm.v2#file
- http://www.w3.org/2000/09/xmldsig#DigestValue
- http://www.w3.org/2000/09/xmldsig#DigestMethod
- http://www.w3.org/2000/09/xmldsig#Transforms
- urn:schemas-microsoft-com:asm.v2#hash
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <file> element [ClickOnce application manifest]
- manifests [ClickOnce], file element
ms.assetid: 56e3490c-eed5-4841-b1bf-eefe778b6ac9
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 88fce548d5adbd6d4dc930db767fd3e52690490b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148771"
---
# <a name="ltfilegt-element-clickonce-application"></a>&lt;&gt;elemento File (aplicativo ClickOnce)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Identifica todos os arquivos não assembly baixados e usados pelo aplicativo.  
  
## <a name="syntax"></a>Syntax  
  
```  
<file  
    name  
    size  
    group  
    optional  
    writeableType  
>  
    <typelib  
        tlbid  
        version  
        helpdir  
        resourceid  
        flags  
    />  
    <comClass  
        clsid  
        description  
        threadingModel  
        tlbid  
        progid  
        miscStatus  
        miscStatusIcon  
        miscStatusContent  
        miscStatusDocPrint  
        miscStatusThumbnail  
    />  
    <comInterfaceExternalProxyStub  
        iid  
        baseInterface  
        numMethods  
        name  
        tlbid  
        proxyStubClass32  
    />  
    <comInterfaceProxyStub  
        iid  
        baseInterface  
        numMethods  
        name  
        tlbid  
        proxyStubClass32  
    />  
    <windowClass  
        versioned  
    />  
</file>  
```  
  
## <a name="elements-and-attributes"></a>Elementos e atributos  
 O elemento `file` é opcional. O elemento tem os atributos a seguir.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`name`|Obrigatórios. Identifica o nome do arquivo.|  
|`size`|Obrigatórios. Especifica o tamanho, em bytes, do arquivo.|  
|`group`|Opcional, se o `optional` atributo não for especificado ou definido como `false` ; obrigatório se `optional` for `true` . O nome do grupo ao qual este arquivo pertence. O nome pode ser qualquer valor de cadeia de caracteres Unicode escolhido pelo desenvolvedor e é usado para baixar arquivos sob demanda com a <xref:System.Deployment.Application.ApplicationDeployment> classe.|  
|`optional`|Opcional. Especifica se esse arquivo deve ser baixado quando o aplicativo é executado pela primeira vez ou se o arquivo deve residir apenas no servidor até que o aplicativo o solicite sob demanda. Se `false` ou indefinido, o arquivo é baixado quando o aplicativo é executado pela primeira vez ou instalado. Se `true` , um `group` deve ser especificado para que o manifesto do aplicativo seja válido. `optional` Não poderá ser verdadeiro se `writeableType` for especificado com o valor `applicationData` .|  
|`writeableType`|Opcional. Especifica que esse arquivo é um arquivo de dados. Atualmente, o único valor válido é `applicationData` .|  
  
## <a name="typelib"></a>typelib  
 O `typelib` elemento é um filho opcional do elemento file. O elemento descreve a biblioteca de tipos que pertence ao componente COM. O elemento tem os atributos a seguir.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`tlbid`|Obrigatórios. O GUID atribuído à biblioteca de tipos.|  
|`version`|Obrigatórios. O número de versão da biblioteca de tipos.|  
|`helpdir`|Obrigatórios. O diretório que contém os arquivos de ajuda para o componente. Pode ser de comprimento zero.|  
|`resourceid`|Opcional. A representação de cadeia de caracteres hexadecimal do identificador de localidade (LCID). É um a quatro dígitos hexadecimais sem um prefixo 0x e sem zeros à esquerda. O LCID pode ter um identificador de subidioma neutro.|  
|`flags`|Opcional. A representação de cadeia de caracteres dos sinalizadores de biblioteca de tipos para esta biblioteca de tipos. Especificamente, deve ser um "RESTRICTED", "CONTROL", "HIDDEN" e "HASDISKIMAGE".|  
  
## <a name="comclass"></a>comClass  
 O `comClass` elemento é um filho opcional do `file` elemento, mas é necessário se o [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo contiver um componente com, ele pretende implantar usando com livre de registro. O elemento tem os atributos a seguir.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`clsid`|Obrigatórios. A ID de classe do componente COM expresso como um GUID.|  
|`description`|Opcional. O nome da classe.|  
|`threadingModel`|Opcional. O modelo de Threading usado por classes COM em processo. Se essa propriedade for nula, nenhum modelo de Threading será usado. O componente é criado no thread principal do cliente e as chamadas de outros threads são empacotadas para esse thread. A lista a seguir mostra os valores válidos:<br /><br /> `Apartment`, `Free`, `Both` e `Neutral`.|  
|`tlbid`|Opcional. GUID da biblioteca de tipos para este componente COM.|  
|`progid`|Opcional. Identificador programático dependente de versão associado ao componente COM. O formato de a `ProgID` é `<vendor>.<component>.<version>` .|  
|`miscStatus`|Opcional. Duplicatas no manifesto do assembly as informações fornecidas pela `MiscStatus` chave do registro. Se os valores dos `miscStatusIcon` `miscStatusContent` atributos,, `miscStatusDocprint` ou `miscStatusThumbnail` não forem encontrados, o valor padrão correspondente listado em `miscStatus` será usado para os atributos ausentes. O valor pode ser uma lista delimitada por vírgula dos valores de atributo da tabela a seguir. Você pode usar esse atributo se a classe COM for uma classe OCX que requer `MiscStatus` valores de chave do registro.|  
|`miscStatusIcon`|Opcional. Duplicatas no manifesto do assembly as informações fornecidas pelo DVASPECT_ICON. Ele pode fornecer um ícone de um objeto. O valor pode ser uma lista delimitada por vírgula dos valores de atributo da tabela a seguir. Você pode usar esse atributo se a classe COM for uma classe OCX que requer `Miscstatus` valores de chave do registro.|  
|`miscStatusContent`|Opcional. Duplicatas no manifesto do assembly as informações fornecidas pelo DVASPECT_CONTENT. Ele pode fornecer uma exibição de documento composto para uma tela ou impressora. O valor pode ser uma lista delimitada por vírgula dos valores de atributo da tabela a seguir. Você pode usar esse atributo se a classe COM for uma classe OCX que requer `MiscStatus` valores de chave do registro.|  
|`miscStatusDocPrint`|Opcional. Duplicatas no manifesto do assembly as informações fornecidas pelo DVASPECT_DOCPRINT. Ele pode fornecer uma representação de objeto que possa ser exibida na tela como se fosse impressa em uma impressora. O valor pode ser uma lista delimitada por vírgula dos valores de atributo da tabela a seguir. Você pode usar esse atributo se a classe COM for uma classe OCX que requer `MiscStatus` valores de chave do registro.|  
|`miscStatusThumbnail`|Opcional. Duplicatas em um manifesto de assembly as informações fornecidas pelo DVASPECT_THUMBNAIL. Ele pode fornecer uma miniatura de um objeto exibível em uma ferramenta de navegação. O valor pode ser uma lista delimitada por vírgula dos valores de atributo da tabela a seguir. Você pode usar esse atributo se a classe COM for uma classe OCX que requer `MiscStatus` valores de chave do registro.|  
  
## <a name="cominterfaceexternalproxystub"></a>comInterfaceExternalProxyStub  
 O `comInterfaceExternalProxyStub` elemento é um filho opcional do `file` elemento, mas pode ser necessário se o [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo contiver um componente com, ele pretende implantar usando com livre de registro. O elemento contém os atributos a seguir.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`iid`|Obrigatórios. A ID de interface (IID) que é servida por esse proxy. A IID deve ter chaves ao redor dela.|  
|`baseInterface`|Opcional. A IID da interface da qual a interface referenciada por `iid` é derivada.|  
|`numMethods`|Opcional. O número de métodos implementados pela interface.|  
|`name`|Opcional. O nome da interface como aparecerá no código.|  
|`tlbid`|Opcional. A biblioteca de tipos que contém a descrição da interface especificada pelo `iid` atributo.|  
|`proxyStubClass32`|Opcional. Mapeia um IID para um CLSID em DLLs de proxy de 32 bits.|  
  
## <a name="cominterfaceproxystub"></a>comInterfaceProxyStub  
 O `comInterfaceProxyStub` elemento é um filho opcional do `file` elemento, mas pode ser necessário se o [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo contiver um componente com, ele pretende implantar usando com livre de registro. O elemento contém os atributos a seguir.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`iid`|Obrigatórios. A ID de interface (IID) que é servida por esse proxy. A IID deve ter chaves ao redor dela.|  
|`baseInterface`|Opcional. A IID da interface da qual a interface referenciada por `iid` é derivada.|  
|`numMethods`|Opcional. O número de métodos implementados pela interface.|  
|`Name`|Opcional. O nome da interface como aparecerá no código.|  
|`Tlbid`|Opcional. A biblioteca de tipos que contém a descrição da interface especificada pelo `iid` atributo.|  
|`proxyStubClass32`|Opcional. Mapeia um IID para um CLSID em DLLs de proxy de 32 bits.|  
|`threadingModel`|Opcional. Opcional. O modelo de Threading usado por classes COM em processo. Se essa propriedade for nula, nenhum modelo de Threading será usado. O componente é criado no thread principal do cliente e as chamadas de outros threads são empacotadas para esse thread. A lista a seguir mostra os valores válidos:<br /><br /> `Apartment`, `Free`, `Both` e `Neutral`.|  
  
## <a name="windowclass"></a>windowClass  
 O `windowClass` elemento é um filho opcional do `file` elemento, mas pode ser necessário se o [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplicativo contiver um componente com, ele pretende implantar usando com livre de registro. O elemento refere-se a uma classe de janela definida pelo componente COM que deve ter uma versão aplicada a ela. O elemento contém os atributos a seguir.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`versioned`|Opcional. Controla se o nome da classe de janela interna usado no registro contém a versão do assembly que contém a classe de janela. O valor desse atributo pode ser `yes` ou `no` . O padrão é `yes`. O valor `no` só deve ser usado se a mesma classe de janela for definida por um componente lado a lado e um componente equivalente não lado a lado e você quiser tratá-los como a mesma classe de janela. Observe que as regras usuais sobre o registro de classe de janela se aplicam — somente o primeiro componente que registra a classe Window poderá registrá-la, pois ela não tem uma versão aplicada a ela.|  
  
## <a name="hash"></a>hash  
 O `hash` elemento é um filho opcional do `file` elemento. O `hash` elemento não tem atributos.  
  
 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] usa um hash de algoritmo de todos os arquivos em um aplicativo como uma verificação de segurança, para garantir que nenhum dos arquivos seja alterado após a implantação. Se o `hash` elemento não for incluído, essa verificação não será executada. Portanto, omitir o `hash` elemento não é recomendado.  
  
 Se um manifesto contiver um arquivo sem hash, esse manifesto não poderá ser assinado digitalmente, pois os usuários não poderão verificar o conteúdo de um arquivo sem hash.  
  
## <a name="dsigtransforms"></a>dsig:Transforms  
 O `dsig:Transforms` elemento é um filho obrigatório do `hash` elemento. O `dsig:Transforms` elemento não tem atributos.  
  
## <a name="dsigtransform"></a>dsig:Transform  
 O `dsig:Transform` elemento é um filho obrigatório do `dsig:Transforms` elemento. O `dsig:Transform` elemento tem os atributos a seguir.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Algorithm`|O algoritmo usado para calcular o resumo para este arquivo. Atualmente, o único valor usado pelo [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] é `urn:schemas-microsoft-com:HashTransforms.Identity` .|  
  
## <a name="dsigdigestmethod"></a>dsig:DigestMethod  
 O `dsig:DigestMethod` elemento é um filho obrigatório do `hash` elemento. O `dsig:DigestMethod` elemento tem os atributos a seguir.  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`Algorithm`|O algoritmo usado para calcular o resumo para este arquivo. Atualmente, o único valor usado pelo [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] é `http://www.w3.org/2000/09/xmldsig#sha1` .|  
  
## <a name="dsigdigestvalue"></a>dsig:DigestValue  
 O `dsig:DigestValue` elemento é um filho obrigatório do `hash` elemento. O `dsig:DigestValue` elemento não tem atributos. Seu valor de texto é o hash calculado para o arquivo especificado.  
  
## <a name="remarks"></a>Comentários  
 Esse elemento identifica todos os arquivos não assembly que compõem o aplicativo e, em particular, os valores de hash para verificação de arquivo. Esse elemento também pode incluir dados de isolamento de Component Object Model (COM) associados ao arquivo. Se um arquivo for alterado, o arquivo de manifesto do aplicativo também deverá ser atualizado para refletir a alteração.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir ilustra os `file` elementos em um manifesto de aplicativo para um aplicativo implantado usando o [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] .  
  
```  
<file name="Icon.ico" size="9216">  
  <hash>  
    <dsig:Transforms>  
      <dsig:Transform Algorithm="urn:schemas-microsoft-com:HashTransforms.Identity" />  
    </dsig:Transforms>  
    <dsig:DigestMethod Algorithm="http://www.w3.org/2000/09/xmldsig#sha1" />  
    <dsig:DigestValue>lVoj+Rh6RQ/HPNLOdayQah5McrI=</dsig:DigestValue>  
  </hash>  
</file>  
```  
  
## <a name="see-also"></a>Consulte Também  
 [Manifesto do aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)
