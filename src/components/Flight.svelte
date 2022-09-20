<script>
const formatDate = date => `${date.getDate()}-${date.getMonth() + 1}-${date.getFullYear()}`

const validateDate = (date) => {
    const [day, month, year] = date.split('-')
    const currentYear = new Date().getFullYear()
    return day > 0 && day <= 31 &&
            month > 0 && month <= 12 &&
            year >= currentYear && year < currentYear + 3
}

let oneWayReturn = 'one-way'
let goDate = formatDate(new Date())
const oneWeekInMs = 7 * 24 * 3600000
const nextWeek = new Date().getTime() + oneWeekInMs
let returnDate = formatDate(new Date(nextWeek))

$: disableReturn = oneWayReturn === 'one-way'
$: isBookingEnabled = oneWayReturn === 'one-way'
    ? validateDate(goDate)
    : validateDate(goDate) && validateDate(returnDate)

const handleBooking = () => {
    let message = `Booking ${oneWayReturn} ticket leaving on ${goDate}`
    if (oneWayReturn === 'return') {
        message += ` coming back on ${returnDate}`
    }
    alert(message)
}

</script>
<h2>Flight</h2>

<div>
    <select bind:value={oneWayReturn}>
        <option value="one-way">one-way flight</option>
        <option value="return">return flight</option>
    </select><br/>

    <input
        bind:value={goDate}
        class={validateDate(goDate) ? '' : 'error'}
    /><br/>
    <input
        disabled={disableReturn}
        class={validateDate(returnDate) ? '' : 'error'}
        bind:value={returnDate}
    /><br/>

    <button
        disabled={!isBookingEnabled}
        on:click={handleBooking}>Book</button>
</div>

<style>
input.error {
    background: red
}
</style>

