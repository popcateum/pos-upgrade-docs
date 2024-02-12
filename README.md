# POS 전환

### description
> 이곳은 팝캣티움 POS 전환에 필요한 내용을 정리하는 곳입니다.

### 준비물
- [geth](https://github.com/ethereum/go-ethereum/releases/tag/v1.11.6) (v1.11.6):  팝캣티움에 맞게 genesis 및 포크 관련 내용 수정 필요
- [deposit contract](https://github.com/ethereum/consensus-specs/blob/master/solidity_deposit_contract/deposit_contract.sol):  비콘체인에 코인 예치
- consensus client:  Prysm, Lighthouse 중에 사용하기 편한걸로 선택
- beacon explorer: beaconcha.in, ethstakers중 사용하기 편한걸로 선택

### 참고 문서
- pos: https://ethereum.org/developers/docs/consensus-mechanisms/pos
- lighthouse: https://lighthouse-book.sigmaprime.io/
- prysm: https://docs.prylabs.network/docs/getting-started
- beacon explorer: https://github.com/gobitfly/eth2-beaconchain-explorer
- ethstakers: https://github.com/ethstakersclub/ethstakersclub
- paris upgrade: https://github.com/ethereum/execution-specs/blob/master/network-upgrades/mainnet-upgrades/paris.md
- EIP-3675: https://eips.ethereum.org/EIPS/eip-3675

### 작업순서
1. geth를 팝캣티움에 맞게 수정
2. pos 전환 하드포크 내용 추가
3. 팝캣티움에 deposit 컨트랙트 배포
4. consensus 클라이언트에 deposit 컨트랙트, 체인id 등 필요 변수값 넣어서 실행
5. 실행노드와 합의노드 연결 확인
6. 설정해둔 시간에 pos 전환 되는지 확인
7. 각 클라이언트 정상 작동 하는지 확인
8. 비콘 체인 익스플로러 연동