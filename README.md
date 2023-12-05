# get-all-documents-firestore-swift-5
## get all documents firestore swift 5
### [Get data with Cloud Firestore](https://firebase.google.com/docs/firestore/query-data/get-data) <br><br>

![image](https://github.com/Experimenters1/get-all-documents-firestore-swift-5/assets/64000769/b160ae15-6c40-41bb-b2c8-5681395a8f50) <br><br>

```swift
import UIKit
import FirebaseCore
import FirebaseFirestore


class Look__Photos: UIViewController {

   let db = Firestore.firestore()
   
    
    override func viewDidLoad() {
        super.viewDidLoad()

       db.collection("users").getDocuments() { (querySnapshot, err) in
          if let err = err {
            print("Error getting documents: \(err)")
          } else {
            for document in querySnapshot!.documents {
              print("\(document.documentID) => \(document.data())")
            }
          }
        }
 }
```


![image](https://github.com/Experimenters1/get-all-documents-firestore-swift-5/assets/64000769/21a41800-bb38-4b6f-b030-c8d9c84ec07d) <br><br>

```swift
import UIKit
import FirebaseCore
import FirebaseFirestore


class Look__Photos: UIViewController {

  
   
    
    override func viewDidLoad() {
        super.viewDidLoad()

 FirebaseManager.shared.firestore.collection("users").getDocuments { (querySnapshot, error) in
            if let error = error {
                print("Error getting documents: \(error)")
            } else {
                for document in querySnapshot!.documents {
                    if let profileImageUrl = document.data()["profileImageUrl"] as? String {
                        print("Profile Image URL for user \(document.documentID): \(profileImageUrl)")
                        print()
                        print("--------------------")
                    } else {
                        print("Profile Image URL not found for user \(document.documentID)")
                    }
                }
            }
        }
 }

```

![image](https://github.com/Experimenters1/get-all-documents-firestore-swift-5/assets/64000769/ae72b766-3203-4e32-bc82-ddab7e1a762b) <br><br>

```swift
import UIKit
import FirebaseCore
import FirebaseFirestore


class Look__Photos: UIViewController {

  
   
    
    override func viewDidLoad() {
        super.viewDidLoad()

              FirebaseManager.shared.firestore.collection("users").getDocuments { (querySnapshot, error) in
            if let error = error {
                print("Error getting documents: \(error)")
            } else {
                for document in querySnapshot!.documents {
                    if let profileImageUrl = document.data()["profileImageUrl"] as? String,
                       let email = document.data()["email"] as? String {
                        print("User \(document.documentID) - Email: \(email), Profile Image URL: \(profileImageUrl)")
                        print()
                        print("--------------------")
                    } else {
                        print("Data not found for user \(document.documentID)")
                    }
                }
            }
        }
 }
```
![image](https://github.com/Experimenters1/get-all-documents-firestore-swift-5/assets/64000769/9971bad0-44b1-4088-bae4-821f183da30a) <br><br>

```swift
import UIKit
import FirebaseCore
import FirebaseFirestore


class Look__Photos: UIViewController {

  
   
    
    override func viewDidLoad() {
        super.viewDidLoad()

            FirebaseManager.shared.firestore.collection("users").getDocuments { (querySnapshot, error) in
            if let error = error {
                print("Error getting documents: \(error)")
            } else {
                for document in querySnapshot!.documents {
                    if let profileImageUrl = document.data()["profileImageUrl"] as? String,
                       let email = document.data()["email"] as? String {
                        
                        // Tạo một Dictionary để chứa thông tin của mỗi người dùng
                        let userDictionary: [String: Any] = [
                            "userID": document.documentID,
                            "email": email,
                            "profileImageUrl": profileImageUrl
                        ]
                        
                        // In ra thông tin của mỗi người dùng dưới dạng Dictionary
                        print("User Dictionary: \(userDictionary)")
                         print()
                        print("--------------------")
                    } else {
                        print("Data not found for user \(document.documentID)")
                    }
                }
            }
        }

 }
```
![image](https://github.com/Experimenters1/get-all-documents-firestore-swift-5/assets/64000769/fa8c832b-62e4-4081-a813-34dfda9ac1a3) <br><br>

![image](https://github.com/Experimenters1/get-all-documents-firestore-swift-5/assets/64000769/dade034a-3524-4a8e-b7a7-617a9fb30ca6) <br><br>

![image](https://github.com/Experimenters1/get-all-documents-firestore-swift-5/assets/64000769/f0b8c491-014c-413b-9a55-0fbc7a4dedec) <br><br>

Để sửa đổi trực tiếp một tài liệu trong **Firestore bằng Swift**, bạn cần sử dụng **Firestore SDK của Firebase**. Dưới đây là một ví dụ cách bạn có thể thực hiện điều này:
```swift
import FirebaseFirestore

// Đường dẫn của tài liệu bạn muốn sửa đổi
let documentPath = "users/user-1"

// Tham chiếu đến Firestore
let db = Firestore.firestore()

// Thực hiện truy vấn để cập nhật trường "name" trong tài liệu
db.document(documentPath).setData(["name": "Huy"], merge: true) { (error) in
    if let error = error {
        print("Lỗi khi cập nhật dữ liệu: \(error.localizedDescription)")
    } else {
        print("Dữ liệu đã được cập nhật thành công.")
    }
}
```
![image](https://github.com/Experimenters1/get-all-documents-firestore-swift-5/assets/64000769/d7a1ee61-ef2b-454b-b3eb-02038f97dfdb)<br><br>







