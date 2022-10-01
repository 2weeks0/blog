# [TypeScript] 교차 타입 (Intersection Types)

- 교차 타입은 여러 타입을 하나로 결합하는 타입이다.
- 예를 들어, `Persion & Serializable & Loggable`은 `Person`과 `Serializable`, `Loggable` 세 가지 타입의 모든 멤버를 가진다.

```typescript
interface ErrorHandling {
  success: boolean;
  error?: { message: string };
}

interface ArtworksData {
  artworks: { title: string }[];
}

interface ArtistsData {
  artists: { name: string }[];
}

// 이 인터페이스들은
// 하나의 에러 핸들링과 자체 데이터로 구성됩니다.

type ArtworksResponse = ArtworksData & ErrorHandling;
type ArtistsResponse = ArtistsData & ErrorHandling;

const handleArtistsResponse = (response: ArtistsResponse) => {
  if (response.error) {
    console.error(response.error.message);
    return;
  }

  console.log(response.artists);
};
```

`handleArtistsResponse` 함수는 `ArtistsResponse` 타입의 변수를 파라미터로 갖는다.

이는 `ArtistsData` & `ErrorHandling` 타입으로 `ArtistsData` 타입의 `artists: { name: string }[]` 멤버와 `ErrorHandling` 의 `success: boolean;`, `error?: { message: string };` 멤버를 모두 갖게 된다.