<template>
<div>
  <div style="text-align: center">
			회원가입
		</div>
		<div>
			<ul class=ul>
				<li class=li>
				<label class=font>아이디</label>
					<input type="text" name="id" class=box>
				</li>
				<li class=li>
				<label class=font>비밀번호</label>
					<input type="password" name="pw" class=box>
				</li>
				<li class=li>
				<label class=font>비밀번호 확인</label>
					<input type="password" name="pw_ok" class=box>
				</li>
				<li class=li>
				<label class=font>이름</label>
					<input type="text" name="name" class=box>
				</li>
				<li class=li>
				<label class=font>이메일</label>
					<input type="text" name="email" class=box>
				</li>
				<li class=li>
				<label class=font>휴대폰번호</label>
					<input type="text" name="tel" class=box>
					<button>인증번호 받기</button>
				</li>
				<li class=li>
				<label class=font>SMS 인증번호</label>
					<input type="text" name="name" class=box>
					<button>인증번호 확인</button>
				</li>
			</ul>
			<ul style="padding: 20px 10px; list-style:none;">
				<li>
					<label style="font-size:15px; font-weight: bold;">
						<input type="checkbox" value="Y">
						" 14세 이상입니다."
						<font color="red">(필수)</font>
					</label>
				</li>
				<li style="margin-left:25px; font-size:12px;">
					회원가입에 필요한 최소한의 정보만 입력 받음으로써, 고객님의 개인정보 수집을 최소화하고
					편리한 회원가입을 제공합니다.
				</li>
			</ul>
		</div>
		<div>
			<div class=border style="font-weight: bold; height:20px;">
				<label>
					<input type="checkbox" name="aa" value="Y">
					전체동의
				</label>
			</div>
			<div class=border>
				<input type="checkbox" name="bb" value="Y">이용약관
				<input type="checkbox" name="cc" value="Y">개인정보 수집 및 이용 안내
				<input type="checkbox" name="dd" value="Y">개인정보 처리위탁
			</div>
			<div class=border>
				<input type="checkbox" name="ee" value="Y">마케팅 수신동의<br/><br/>
				쇼핑몰에서 제공하는 신상품 소식과 하일쿠폰을 무상으로 보내드립니다!<br/>
				단, 상품 구매 정보는 수신동의 여부 관계없이 발송됩니다.<br/>
				제공 동의를 하지 않으셔도 서비스 이용에는 문제가 없습니다.
			</div>
		</div>
		<button>가입하기</button>
  </div>
</template>

<script>
export default {
  name: 'Join',
  props: {
    msg: String
  }
}
</script>

<style scoped>
/* 회원가입 박스 */
.ul{
	border-top: 1px solid black;
	display: block;
	list-style: none;
}
.li{
	border-top: 1px solid #BDBDBD;
	border-bottom: 1px solid #BDBDBD;
	padding: 15px 0px;
}
/* 회원가입 박스 */
.box{
	display: inline-block;
	width: 300px;
	height: 40px;
	box-sizing: border-box;
	border: 1px solid #848484;
	
}
.box1{
	display: linline-block;
	width: 90px;
	height: 40px;
	box-sizing: border-box;
	border: 1px solid #848484;
	margin: 0px 4px;
}
/* 회원가입 폰트 */
.font{
	font-size: 14px;
	font-weight: bold;
	display: inline-block;
	width: 100px;
}
/* 약관동의 */
.border{
	border: 1px solid #BDBDBD;
}
/* 가입 박스 */
.box2{
	display: block;
	width: 400px;
	height: 100px;
	box-sizing: border-box;
	
}
</style>