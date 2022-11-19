<img src="https://ik.imagekit.io/ghmg33v8b/projects/nlw-world-cup/nlw-world-cup_CU7S4LwV0.svg?ik-sdk-version=javascript-1.4.3&updatedAt=1668870447980" width="500" />

This repository was developed during the **next level week cup**, promoted by the **Rocketseat team**, in order to cover more knowledge related to the **Javascript** stack with **React** and **Next.JS** technologies for the Web, **React Native** and **Expo** for the Mobile App, in addition to from **Node JS** and **Fastify** to the backend server.  All technologies used **Typescript**.

# 💻 Web

## Screens

![Image of home screen](https://ik.imagekit.io/ghmg33v8b/projects/nlw-world-cup/index-page-of-web_blS1y8JEQ.png?ik-sdk-version=javascript-1.4.3&updatedAt=1668870490961 "Home Screen")

## Technologies
- [React JS](https://reactjs.org/)
- [Next JS](https://nextjs.org/)
- [Axios](https://axios-http.com/ptbr/docs/intro)
- [TypeScript](https://www.typescriptlang.org/)
- [Tailwindcss](https://tailwindcss.com/)

# 📱 Mobile

## Screens

<center>
<img src="https://ik.imagekit.io/ghmg33v8b/projects/nlw-world-cup/splash-screen_uKIAF0BOp.png?ik-sdk-version=javascript-1.4.3&updatedAt=1668871210925" width="145"> <img src="https://ik.imagekit.io/ghmg33v8b/projects/nlw-world-cup/login_2Yn-f5V3x.png?ik-sdk-version=javascript-1.4.3&updatedAt=1668872533959" width="145"> <img src="https://ik.imagekit.io/ghmg33v8b/projects/nlw-world-cup/new-sweepstakes_5DzxsIBAG.png?ik-sdk-version=javascript-1.4.3&updatedAt=1668871363282" width="145" /> <img src="https://ik.imagekit.io/ghmg33v8b/projects/nlw-world-cup/new-sweepstake-loading_BoAFBjVFn.png?ik-sdk-version=javascript-1.4.3&updatedAt=1668872534373" width="145" />
 <img src="https://ik.imagekit.io/ghmg33v8b/projects/nlw-world-cup/my-sweepstakes_Hyuz9Kr58.png?ik-sdk-version=javascript-1.4.3&updatedAt=1668872534524" width="145" /> <img src="https://ik.imagekit.io/ghmg33v8b/projects/nlw-world-cup/sweepstakes-details_xBt9E_Igfm?ik-sdk-version=javascript-1.4.3&updatedAt=1668871903648" width="145" /> <img src="https://ik.imagekit.io/ghmg33v8b/projects/nlw-world-cup/search-my-sweepstakes_Xcu_sTa8m.png?ik-sdk-version=javascript-1.4.3&updatedAt=1668872907934" width="145" /> <img src="https://ik.imagekit.io/ghmg33v8b/projects/nlw-world-cup/sweepstakes-ranking_3jpBxvLG_.png?ik-sdk-version=javascript-1.4.3&updatedAt=1668872534522" width="145" /> 
 </center>

## Technologies
- [React Native](https://reactnative.dev/)
- [Expo](https://docs.expo.dev/)
- [React Navigation](https://reactnavigation.org/)
- [Native Base](https://nativebase.io/)
- [Axios](https://axios-http.com/ptbr/docs/intro)
- [TypeScript](https://www.typescriptlang.org/)
- [Dayjs](https://day.js.org/)
- [Phosphor React Native](https://www.npmjs.com/package/phosphor-react-native)
# 🔋 Server
## Routes

### Auth

**GET**  — "/me"

_Get JWT informations_

_**Bearer token required**_

response:

```
{
	"user": {
		"name": string,
		"avatarUrl": string,
		"sub": string,
		"iat": number,
		"exp": number
	}
}
```
<br>

**POST**  — "/users"

_Sign In / Sign Up with access_token that can be obtained by Google OAuth2_

request: 

```
{
	"access_token": string
}
```

response:

```
{
	"token": string
}
```
<hr>

### Game

**GET**  — "/pools/:id/games"

_List games by pool id_

_**Bearer token required**_

route params:

`id: string`


response:

```
{
	"games": [
		{
			"id": string,
			"date": DateTime,
			"firstTeamCountryCode": string,
			"secondTeamCountryCode": string,
			"guess": {
				"id": string,
				"firstTeamPoints": number,
				"secondTeamPoints": number,
				"createdAt": DateTime,
				"gameId": string,
				"participantId": string
			}
		},
		{
			"id": string,
			"date": DateTime,
			"firstTeamCountryCode": string,
			"secondTeamCountryCode": string,
			"guess": null
		}
	]
}
```

<hr>

### Guess

**GET**  — "/guesses/count"

_Get count of created guesses_

response:

```
{
	"count": number
}
```
<br>

**POST** — "/pools/:poolId/games/:gameId/guesses"

_Create a guess in the pool and games by yours ids_

_**Bearer token required**_

route params:

`poolId: string`
`gameId: string`

request:

```
{
	"firstTeamPoints": number,
	"secondTeamPoints": number
}
```

<hr>

### Pool

**GET**  — "/pools/count"

_Get count of created pools_

response:

```
{
	"count": number
}
```
<br>

**GET**  — "/pools"

_Get pools that my user is participating in_

_**Bearer token required**_

response:

```
{
	"pools": [
		{
			"id": string,
			"title": string,
			"code": string,
			"createdAt": DateTime,
			"ownerId": string,
			"participants": [
				{
					"id": string,
					"user": {
						"avatarUrl": string
					}
				}
			],
			"owner": {
				"id": string,
				"name": string
			},
			"_count": {
				"participants": number
			}
		}
	]
}
```
<br>

**GET**  — "/pools/:id"

_Get specific pool by your id_

_**Bearer token required**_

route params:

`id: string`

response:

```
{
	"pool": {
		"id": string,
		"title": string,
		"code": string,
		"createdAt": DateTime,
		"ownerId": string,
		"participants": [
			{
				"id": string,
				"user": {
					"avatarUrl": string
				}
			}
		],
		"owner": {
			"id": string,
			"name": string
		},
		"_count": {
			"participants": number
		}
	}
}
```

<br>

**POST**  — "/pools"

_Create a new pool_

_**Bearer token optional (?)**_

```
{
	"title": string
}
```

response:

```
{
	"code": string
}
```
<br>

**POST**  — "/pools/join"

_Join in a existant pool_

_**Bearer token required**_

request:

```
{
	"code": string
}
```
<hr>

### User

**GET** — "/users/count"

_Get count of registered users in the system_

response:

```
{
	"count": number
}
```

## Technologies

- [Node JS](https://nodejs.org/en/)
- [Fastify](https://www.fastify.io/)
- [Prisma](https://www.prisma.io/)
- [Zod](https://zod.dev/)
- [Short Unique Id](https://shortunique.id/)

<br>

_Constant Learning_ 🚀💜