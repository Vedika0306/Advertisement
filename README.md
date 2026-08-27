# Advertisement
const dateInput = document.getElementById("date");

dateInput.min = new Date().toISOString().split("T")[0];

document.getElementById("bookingForm").addEventListener("submit", function(e) {
    e.preventDefault();

    const name = document.getElementById("name").value.trim();
    const service = document.getElementById("service").value;
    const date = document.getElementById("date").value;
    const time = document.getElementById("time").value;
    const notice = document.getElementById("notice");

    const formattedDate = new Date(date + "T00:00:00")
        .toLocaleDateString("en-IN", {
            day: "numeric",
            month: "long",
            year: "numeric"
        });

    notice.style.display = "block";

    notice.textContent =
        `Thank you, ${name}! Your ${service} appointment request 
        for ${formattedDate} at ${time} has been recorded.`;

    this.reset();

    dateInput.min = new Date().toISOString().split("T")[0];
});
