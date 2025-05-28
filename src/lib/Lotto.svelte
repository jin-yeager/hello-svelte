<script>
  // 1~45 배열을 직접 나열
  const arr45 = [
    1,2,3,4,5, 6,7,8,9,10,
    11,12,13,14,15, 16,17,18,19,20,
    21,22,23,24,25,26,27,28,29,30,
    31,32,33,34,35,36,37,38,39,40,
    41,42,43,44,45
  ];

  // 개별 로또 번호 바인딩 변수
  let l1 = '__';
  let l2 = '__';
  let l3 = '__';
  let l4 = '__';
  let l5 = '__';
  let l6 = '__';

  function generateLotto() {
    // arr45 복사본 생성
    const numbers = [...arr45];

    // 1000번 셔플
    for (let i = 0; i < 1000; i++) {
      const rnd = Math.floor(Math.random() * 45);
      const temp = numbers[0];
      numbers[0] = numbers[rnd];
      numbers[rnd] = temp;
    }

    // inline 버블 정렬: numbers의 처음 6개만 정렬
    for (let i = 0; i < 5; i++) {
      for (let j = 0; j < 5 - i; j++) {
        if (numbers[j] > numbers[j + 1]) {
          const temp2 = numbers[j];
          numbers[j] = numbers[j + 1];
          numbers[j + 1] = temp2;
        }
      }
    }

    // 정렬된 상위 6개를 각 변수에 할당
    l1 = numbers[0];
    l2 = numbers[1];
    l3 = numbers[2];
    l4 = numbers[3];
    l5 = numbers[4];
    l6 = numbers[5];
  }
</script>

<table>
  <tbody>
  <tr>
    <td><span>{l1}</span></td>
    <td><span>{l2}</span></td>
    <td><span>{l3}</span></td>
    <td><span>{l4}</span></td>
    <td><span>{l5}</span></td>
    <td><span>{l6}</span></td>
  </tr>
  <tr>
    <td colspan="6">
      <button on:click={generateLotto}>로또 생성하기</button>
    </td>
  </tr>
  </tbody>
</table>

<style>
  table, tr, td {
    border: 1px solid grey;
  }
</style>
