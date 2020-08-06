---
title: ProcessId クラス (SqlService クラス) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
api_name:
- ProcessId Class (SqlService Class)
api_location:
- sqlmgmproviderxpsp2up.mof
topic_type:
- apiref
helpviewer_keywords:
- ProcessId property
ms.assetid: 99b5a2e9-b44a-48a0-993e-04bd15c7fef4
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 7c4c40eea826b5009e52d26b1d930eaf5febbcdb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/04/2020
ms.locfileid: "87640804"
---
# <a name="processid-class-sqlservice-class"></a>ProcessId クラス (SqlService クラス)
  サービスを一意に識別するシステム プロセス ID を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
object  
.ProcessId [= value]  
```  
  
## <a name="parts"></a>指定項目  
 *object*  
 サービスを表す [SqlService クラス](sqlservice-class.md) オブジェクト。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 プロセスを一意に識別する ID を指定する `uint32` 値。  
  
## <a name="remarks"></a>解説  
  
## <a name="example"></a>例  
  
```  
mysqlservice.ProcessId = 324  
```  
  
## <a name="see-also"></a>参照  
 [サービスの開始および停止](https://technet.microsoft.com/library/ms174886\(v=sql.105\).aspx)  
  
  
