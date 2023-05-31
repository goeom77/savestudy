### Put vs Patch

put과 patch는 수정하는 역할을 한다고 말할 수 있다.

하지만 엄연히 다른 정의와 규약을 가지고 있다.

put을 먼저 알아보자

put메소드는 요청한 URI에 payload에 있는 자원으로 대체하는 메서드이다. 여기서 대상을 저장하기도, 변경하기도 한다는 것을 의미한다. 

case1. 요청한 URI아래에 자원이 존재하지 않는 경우, POST와 마찬가지로 새로운 자원으로 대체하고, 해당 요청이 잘 적용되었다는 200, 204를 통해 알려준다.

PUT은 주로 좋아요와 같은 기능에 잘 사용된다.

```java
@Entity
public class Like {
  
  @Id
  private Long id;
  
  private Long articleId;
  
  private Long userId;
  
  private LikeType likeType;   //** liked or disliked
    
) {
    articleService.update(articleId, user.getId(), request.getLikeType());
    return ResponseEntity.noContent().build();
}
...
// LikeService.java
...
@Transactional
public void update(Long articleId, Long userId, LikeType likeType) {
    Like like = likeRepository.findByArticleIdAndUserId(articleId, userId)
      .map(l -> l.setType(likeType))
      .orElse(new Like(articleId, userId, likeType));

    likeRepository.save(like);
}
```

위와 같이 Like 엔티티는 atricleld(어떤 게시물에 대한 건지), userld(누가 좋아요 한건지), type(좋아요/싫어요) 상태로 가진다.

Patch의 경우 

payload 전체가 아닌, 현재 필요한 모든 필드값을 body에 담아서 보내면 된다.

대신 이렇게 받은 값에 대해서는 DTO를 별도로 만들어 줘야 하고, 새로운 엔티티를 생성할 수 없다는 한계가 있다.

또한 Put은 멱등성을 지키지만 Patch는 멱등성을 지키지 못한다.