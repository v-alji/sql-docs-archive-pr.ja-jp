---
title: Server 要素 (DTA) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Server element
ms.assetid: 9fe0bfb4-3aa6-4eb2-a83e-c0d0e7d4e9f6
author: stevestein
ms.author: sstein
ms.openlocfilehash: ab67e0303c2b629c3774886441474f5ef5b10a43
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87643056"
---
# <a name="server-element-dta"></a>Server 要素 (DTA)
  チューニングするデータベースが置かれているサーバーの識別情報が含まれます。  
  
## <a name="syntax"></a>構文  
  
```  
  
<DTAInput>  
    <Server>  
    ...code removed here...  
    </Server>  
```  
  
## <a name="element-characteristics"></a>要素の特性  
  
|特徴|説明|  
|--------------------|-----------------|  
|**データ型と長さ**|[なし] :|  
|**既定値**|[なし] :|  
|**個数**|必須。`DTAInput` 要素につき 1 個。|  
  
## <a name="element-relationships"></a>要素の関係  
  
|リレーションシップ|要素|  
|------------------|--------------|  
|**親要素**|[DTAInput 要素 &#40;DTA&#41;](dtainput-element-dta.md)|  
|**子要素**|[Server の Name 要素 &#40;DTA&#41;](name-element-for-server-dta.md)<br /><br /> [Server の Database 要素 &#40;DTA&#41;](database-element-for-server-dta.md)|  
  
## <a name="remarks"></a>解説  
 要素に指定できる要素は1つだけ `Server` `DTAInput` です。 この要素は、DTA XML スキーマの **ServerDetailsTypecomplexType** の名前です。 この `Server` 要素を `Configuration` 要素の子要素と混同しないでください。 詳細については、「[Configuration のサーバー要素 &#40;DTA&#41;](server-element-for-configuration-dta.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例は、SERVER001 上の **AdventureWorks** データベースの **Sales.SalesPerson** テーブルを指定する方法を示しています:  
  
```xml  
<Server>  
  <Name>SERVER001</Name>  
  <Database>  
    <Name>AdventureWorks</Name>  
    <Schema>  
      <Name>Sales</Name>  
      <Table>  
        <Name>SalesPerson</Name>  
      </Table>  
    </Schema>  
  </Database>  
</Server  
```  
  
## <a name="see-also"></a>参照  
 [XML 入力ファイル リファレンス &#40;データベース エンジン チューニング アドバイザー&#41;](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
