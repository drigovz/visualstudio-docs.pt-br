---
title: '&lt;&gt;elemento EntryPoint (aplicativo ClickOnce) | Microsoft Docs'
description: O elemento entryPoint identifica o assembly que deve ser executado quando este aplicativo ClickOnce é executado em um computador cliente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- urn:schemas-microsoft-com:asm.v2#commandLine
- urn:schemas-microsoft-com:asm.v2#entryPoint
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- <entryPoint> element [ClickOnce application manifest]
- manifests [ClickOnce], entryPoint element
ms.assetid: 10ad3083-10c1-4189-a870-9bba2eab244f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d5c35d94001ae1e883e2bd76650f248d7e0364d2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893887"
---
# <a name="ltentrypointgt-element-clickonce-application"></a>&lt;&gt;elemento EntryPoint (aplicativo ClickOnce)
Identifica o assembly que deve ser executado quando este [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo é executado em um computador cliente.

## <a name="syntax"></a>Sintaxe

```xml
<entryPoint
   name
>
   <assemblyIdentity
      name
      version
      processorArchitecture
      language
   />
   <commandLine
      file
      parameters
   />
   <customHostRequired />
   <customUX />
</entryPoint>
```

## <a name="elements-and-attributes"></a>Elementos e atributos
 O `entryPoint` elemento é obrigatório e está no `urn:schemas-microsoft-com:asm.v2` namespace. Pode haver apenas um `entryPoint` elemento definido em um manifesto do aplicativo.

 O `entryPoint` elemento tem o atributo a seguir.

|Atributo|Descrição|
|---------------|-----------------|
|`name`|Opcional. Esse valor não é usado pelo .NET Framework.|

 `entryPoint` tem os elementos a seguir.

## <a name="assemblyidentity"></a>assemblyIdentity
 Obrigatório. A função de `assemblyIdentity` e seus atributos são definidos no [ \<assemblyIdentity> elemento](../deployment/assemblyidentity-element-clickonce-application.md).

 O `processorArchitecture` atributo desse elemento e o `processorArchitecture` atributo definido em `assemblyIdentity` outro lugar no manifesto do aplicativo devem corresponder.

## <a name="commandline"></a>commandLine
 Obrigatório. Deve ser um filho do `entryPoint` elemento. Ele não tem nenhum elemento filho e tem os atributos a seguir.

| Atributo | Descrição |
|--------------| - |
| `file` | Obrigatórios. Uma referência local para o assembly de inicialização do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo. Este valor não pode conter barra invertida (/) ou separadores de caminho de barra invertida ( \\ ). |
| `parameters` | Obrigatório. Descreve a ação a ser tomada com o ponto de entrada. O único valor válido é `run` ; se uma cadeia de caracteres em branco for fornecida, `run` será assumida. |

## <a name="customhostrequired"></a>customHostRequired
 Opcional. Se incluído, especifica que essa implantação contém um componente que será implantado dentro de um host personalizado e não é um aplicativo autônomo.

 Se esse elemento estiver presente, os `assemblyIdentity` `commandLine` elementos e também não deverão estar presentes. Se estiverem, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o gerará um erro de validação durante a instalação.

 Este elemento não tem atributos nem filhos.

## <a name="customux"></a>customUX
 Opcional. Especifica que o aplicativo está instalado e mantido por um instalador personalizado e não cria uma entrada de menu Iniciar, atalho ou adicionar ou remover programas.

```xml
<customUX xmlns="urn:schemas-microsoft-com:clickonce.v1" />
```

 Um aplicativo que inclui o elemento customUX deve fornecer um instalador personalizado que usa a <xref:System.Deployment.Application.InPlaceHostingManager> classe para executar operações de instalação. Um aplicativo com este elemento não pode ser instalado clicando duas vezes em seu manifesto ou setup.exe bootstrapper de pré-requisito. O instalador personalizado pode criar entradas de menu Iniciar, atalhos e adicionar ou remover entradas de programas. Se o instalador personalizado não criar uma entrada adicionar ou remover programas, ele deverá armazenar o identificador de assinatura fornecido pela <xref:System.Deployment.Application.GetManifestCompletedEventArgs.SubscriptionIdentity%2A> propriedade e permitir que o usuário desinstale o aplicativo mais tarde chamando o <xref:System.Deployment.Application.InPlaceHostingManager.UninstallCustomUXApplication%2A> método. Para obter mais informações, consulte [Walkthrough: Criando um instalador personalizado para um aplicativo ClickOnce](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md).

## <a name="remarks"></a>Comentários
 Esse elemento identifica o assembly e o ponto de entrada para o [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo.

 Você não pode usar `commandLine` o para passar parâmetros para o seu aplicativo em tempo de execução. Você pode acessar parâmetros de cadeia de caracteres de consulta para uma [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] implantação a partir do aplicativo <xref:System.AppDomain> . Para obter mais informações, consulte [como recuperar informações de cadeia de caracteres de consulta em um aplicativo ClickOnce online](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md).

## <a name="example"></a>Exemplo
 O exemplo de código a seguir ilustra um `entryPoint` elemento em um manifesto de aplicativo para um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo. Este exemplo de código é parte de um exemplo maior fornecido para o tópico [manifesto do aplicativo ClickOnce](../deployment/clickonce-application-manifest.md) .

```xml
<!-- Identify the main code entrypoint. -->
<!-- This code runs the main method in an executable assembly. -->
  <entryPoint>
    <assemblyIdentity
      name="MyApplication"
      version="1.0.0.0"
      language="neutral"
      processorArchitecture="x86" />
    <commandLine file="MyApplication.exe" parameters="" />
  </entryPoint>
```

## <a name="see-also"></a>Confira também
- [Manifesto do aplicativo ClickOnce](../deployment/clickonce-application-manifest.md)
